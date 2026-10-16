# Medical-Agentic-Chatbot

# Start
# create venv
python -m venv .medical-agenticai

# activate venv
.medical-agenticai\scripts\activate

# install dependencies

pip install -r requirements.txt

# to start main app.py
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000

Open http://127.0.0.1:8000. API documentation: http://127.0.0.1:8000/docs. /api/health checks configuration. Run ingest.py once before chatting; it makes paid embedding calls and creates a Pinecone serverless index. The Pinecone index uses 1536 dimensions for text-embedding-3-small. If using a different embedding model, adjust the dimension and use a fresh index.

# Project Structure

- app/config.py — environment and Conda SSL certificate workaround
- app/knowledge.py — Pinecone vector retrieval
- app/agent.py — LangGraph retrieve → route → Tavily (when needed) → answer
- app/main.py — FastAPI, multimodal image observations, Whisper and TTS endpoints
- ingest.py — chunk and embed every readable PDF page
- templates/index.html — UI
- static/style.css, static/app.js — styles and browser controls
- data/medical_book.pdf — user-supplied reference PDF