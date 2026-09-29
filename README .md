<div align="center">

# 🔍 PlagioCheck

### AI-Powered Plagiarism & AI-Content Detection Platform

A full-stack web app that checks text for plagiarism against live web content and flags AI-generated writing — built with a React frontend, Node.js/Express backend, and a Python microservice for NLP-based similarity analysis.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-plagiocheck.vercel.app-4f46e5?style=for-the-badge)](https://plagiocheck.vercel.app)
[![Backend](https://img.shields.io/badge/Backend-Render-46e3b7?style=for-the-badge)](https://plagiocheck-backend.onrender.com)

![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)

[Live Demo](https://plagiocheck.vercel.app) · [Report Bug](../../issues) · [Request Feature](../../issues)

</div>

---

## 📖 About

**PlagioCheck** lets you paste or upload text and instantly checks it for:
- 🌐 **Plagiarism** — cross-references your text against live web content using the Tavily search API, with TF-IDF + cosine similarity scoring
- 🤖 **AI-generated content** — flags writing that looks machine-generated
- ✨ **Sentence-level highlighting** — see exactly which sentences matched, and how closely

Built as an MCA final-year project, then taken from "works on my machine" to a fully deployed 3-tier production app.

> ⚠️ Hosted on free-tier infrastructure — if the app has been idle, the first request can take 30–50s to wake up. Just wait and retry.

---

## ✨ Features

- 🔐 User authentication — email/password (JWT) and Google OAuth
- 📝 Plagiarism check with live web search cross-referencing
- 🎯 Similarity scoring with highlighted matched sentences
- 🤖 Separate AI-content detection mode
- 📊 Check history per user
- 🛡️ Rate-limited API to prevent abuse
- 📱 Responsive, modern UI

---

## 🏗️ Architecture

PlagioCheck runs as three independently deployed services:

```
┌─────────────────┐      ┌──────────────────┐      ┌─────────────────────┐
│   React (Vercel)│ ───▶ │  Node/Express     │ ───▶ │  Python/Flask ML     │
│   Frontend UI    │◀─── │  Backend API       │◀─── │  Similarity Engine   │
└─────────────────┘      │  (Render)          │      │  (Render)             │
                          └─────────┬─────────┘      └───────────┬──────────┘
                                    │                              │
                                    ▼                              ▼
                          ┌──────────────────┐          ┌──────────────────┐
                          │  MongoDB Atlas    │          │  Tavily Search API │
                          │  (users, history)  │          │  (live web results) │
                          └──────────────────┘          └──────────────────┘
```

| Layer | Tech |
|---|---|
| **Frontend** | React, React Router |
| **Backend** | Node.js, Express, Mongoose, Passport (Google OAuth), JWT |
| **ML Service** | Python, Flask, scikit-learn (TF-IDF + cosine similarity), NLTK |
| **Database** | MongoDB Atlas |
| **Web Search** | Tavily API |
| **Deployment** | Vercel (frontend) · Render (backend + ML service) |

---

## 🚀 Getting Started (Local Setup)

### Prerequisites
- Node.js ≥ 18
- Python ≥ 3.10
- A MongoDB connection string (local or Atlas)
- A [Tavily API key](https://tavily.com) (free tier available)

### 1. Clone the repo
```bash
git clone https://github.com/siddharthpatwal26/PlagioCheck.git
cd PlagioCheck
```

### 2. Set up the ML service
```bash
cd ml
pip install -r requirements.txt
cp .env.example .env   # fill in TAVILY_API_KEY
python app.py          # runs on http://localhost:5001
```

### 3. Set up the backend
```bash
cd backend
npm install
cp .env.example .env   # fill in MONGO_URI, JWT_SECRET, ML_SERVICE_URL, etc.
npm start               # runs on http://localhost:5000
```

### 4. Set up the frontend
```bash
cd frontend
npm install
cp .env.example .env   # set REACT_APP_API_URL=http://localhost:5000/api
npm start               # runs on http://localhost:3000
```

---

## 📁 Project Structure

```
PlagioCheck/
├── frontend/     # React app
├── backend/      # Express API (auth, routes, rate limiting)
└── ml/           # Flask microservice (similarity + web-search matching)
```

---

## 🌐 Live Deployment

| Service | URL |
|---|---|
| Frontend | https://plagiocheck.vercel.app |
| Backend API | https://plagiocheck-backend.onrender.com |
| ML Service | https://plagiocheck-ml.onrender.com |

---

## 👤 Author

**Siddharth Patwal**
[GitHub](https://github.com/siddharthpatwal26) · [LinkedIn](https://www.linkedin.com/in/siddharthpatwal26/)

---

## 📄 License

This project is open source and available for educational use.
