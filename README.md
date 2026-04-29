# Enterprise Document Intelligence System (RAG)

A production-grade Retrieval-Augmented Generation (RAG) system designed to enable semantic search and intelligent querying across large-scale enterprise documents using LLMs.

---

## 🚀 Overview

This project implements a scalable and secure document intelligence system that leverages modern LLM pipelines to retrieve, process, and generate context-aware responses from enterprise data.

The system integrates vector search, API-based architecture, and feedback-driven learning to enhance response accuracy and performance.

---

## 🧠 Key Features

- Semantic search across large document collections  
- Optimized vector retrieval with reduced latency (~35%)  
- Secure API access using JWT authentication  
- Modular RAG pipeline using LangChain  
- Metadata-based filtering for precise retrieval  
- Feedback loop for continuous improvement of responses  

---

## 🏗️ Architecture

User Query → FastAPI → LangChain → FAISS → OpenAI → Response

---

## 🛠️ Tech Stack

- Python 3.10+
- LangChain
- FAISS
- FastAPI
- OpenAI GPT
- SQLite / PostgreSQL
- JWT Authentication

---

## 📂 Project Structure

rag-system/
│
├── app/
│   ├── main.py
│   ├── auth.py
│   ├── rag_pipeline.py
│   ├── ingestion.py
│
├── data/
├── faiss_index/
├── db.sqlite
├── requirements.txt
└── README.md

---

## ⚙️ Installation

```bash
git clone https://github.com/your-username/rag-system.git
cd rag-system

python -m venv venv
source venv/bin/activate

pip install -r requirements.txt
```

---

## 📥 Document Ingestion

```python
from langchain.document_loaders import PyPDFLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter

loader = PyPDFLoader("data/sample.pdf")
documents = loader.load()

splitter = RecursiveCharacterTextSplitter(chunk_size=500, chunk_overlap=100)
docs = splitter.split_documents(documents)
```

---

## 🔎 Query Pipeline

```python
from langchain.chains import RetrievalQA
from langchain.chat_models import ChatOpenAI

retriever = vector_db.as_retriever(search_kwargs={"k": 5})
llm = ChatOpenAI(model="gpt-4")

qa = RetrievalQA.from_chain_type(llm=llm, retriever=retriever)

response = qa.run("Your query here")
```

---

## 🌐 API Usage

```bash
uvicorn app.main:app --reload
```

POST /ask

{
  "question": "Explain company policy"
}

---

## 🔐 Authentication

JWT-based secure API access.

---

## 🔁 Feedback Loop

feedback(
    query TEXT,
    response TEXT,
    corrected_response TEXT,
    rating INT
)

---

## 📈 Future Enhancements

- Hybrid search  
- Streaming responses  
- Redis caching  
- Frontend UI  
- Docker deployment  

---

## 📌 License

MIT License
