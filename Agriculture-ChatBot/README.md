# 🌾 AgriGenius AI — Enterprise Agriculture AI Platform

[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Python](https://img.shields.io/badge/Python_3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)

> **AgriGenius AI** is an intelligent, full-stack decision-support and conversational SaaS platform built to empower farmers with real-time agronomic insights, disease diagnostics, weather advisories, mandi market prices, and crop recommendations.

---

## 🌟 Key Features

### 🤖 Intelligent Multilingual AI Chatbot
- **Zero-Shot Intent Classification**: Recognizes 20+ specialized farming intents in real time.
- **Multilingual Support**: Supports English, Hindi, and Gujarati scripts with spaCy and fallback tokenization.
- **RAG Knowledge Retrieval**: Retrieves contextual agricultural practices using **E5 Multilingual Embeddings** and **ChromaDB**.

### 🌾 Crop & Fertilizer Advisory System
- **ML Model Registry**: Dynamic model switching for crop recommendation, fertilizer selection, and yield prediction.
- **Precision Agronomy**: Leverages N-P-K soil profiles, climate conditions, and historical trends for tailored suggestions.

### 🌦️ Hyperlocal Weather & Farming Schedules
- **Weather Advisory Engine**: Computes actionable guidance for irrigation, pesticide application, and harvest windows based on wind, humidity, and temperature.
- **Location Auto-Detection**: GPS & IP-based reverse geocoding to provide location-specific advice.

### 📊 Mandi Market Price Intelligence
- **Real-Time Mandi Trends**: Up-to-date modal prices across commodities and regional mandis.
- **Price Forecasting**: Helps farmers decide the optimal time and market to sell their produce.

### 🌿 Plant Health Diagnostics
- **Leaf Disease Detection**: Computer vision classification for crop foliage health.
- **OCR Label Reader & Soil Reports**: Automated dosage extraction from fertilizer packaging and test reports.
- **Voice STT & TTS**: Multilingual voice interaction for accessible, hands-free usage in the field.

---

## 🏗️ System Architecture

```
   ┌────────────────────────────────────────────────────────┐
   │               Farmer & Admin UI (React + Vite)         │
   └───────────────────────────┬────────────────────────────┘
                               │ REST / JSON (Port 8000)
                               ▼
   ┌────────────────────────────────────────────────────────┐
   │                  FastAPI Gateway & Router              │
   ├───────────────────────────┬────────────────────────────┤
   │  NLP & Intent Engine      │  RAG Retrieval Chain       │
   │  (spaCy, HF Classifiers)  │  (E5 Embeddings + Chroma)  │
   ├───────────────────────────┼────────────────────────────┤
   │  Plant Health Service     │  Smart Agri Services       │
   │  (Vision, OCR, Voice)     │  (Weather, Mandi Prices)   │
   ├───────────────────────────┴────────────────────────────┤
   │                 ML Model Management Registry           │
   │           (Random Forest, XGBoost, CatBoost)           │
   └─────────────┬───────────────────────────┬──────────────┘
                 │                           │
                 ▼                           ▼
        ┌─────────────────┐         ┌─────────────────┐
        │  MongoDB Atlas  │         │    Chroma DB    │
        │  (User & Farms) │         │ (Vector Store)  │
        └─────────────────┘         └─────────────────┘
```

---

## 📂 Project Structure

```
nlpchatbot/
├── Agriculture-ChatBot/
│   ├── backend/
│   │   ├── app/
│   │   │   ├── api/v1/         # REST API endpoints (NLP, Weather, Mandi, Models)
│   │   │   ├── ai/             # Agent, RAG, NLP, ML registries, and tools
│   │   │   └── core/           # Security, MongoDB connection, config
│   │   ├── requirements.txt    # Python dependencies
│   │   └── Dockerfile          # Backend container specification
│   ├── frontend/
│   │   ├── src/
│   │   │   ├── components/     # UI components (Layout, Cards, Navigation)
│   │   │   ├── contexts/       # Auth and Location providers
│   │   │   ├── pages/          # Dashboard, Chatbot, Weather, Marketplace
│   │   │   └── services/       # API integration services
│   │   ├── package.json        # Frontend dependencies
│   │   └── vite.config.js      # Vite build & proxy config
│   ├── docker-compose.yml      # Multi-container orchestration
│   └── .env.example            # Environment configuration template
├── .gitignore
└── README.md
```

---

## 🚀 Quickstart Guide

### 1. Prerequisites
- **Python**: 3.10 or higher
- **Node.js**: v18 or higher (with npm)
- **Git**

---

### 2. Backend Setup (FastAPI)

1. Navigate to the backend directory:
   ```bash
   cd Agriculture-ChatBot/backend
   ```

2. Create and activate a Python virtual environment:
   ```powershell
   # Windows PowerShell
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```
   ```bash
   # macOS / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables:
   ```bash
   # From the project root or backend folder
   cp ../.env.example .env
   ```

5. Launch the backend server:
   ```bash
   uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
   ```

- 📡 **API Base URL**: `http://127.0.0.1:8000`
- 📑 **Swagger API Docs**: `http://127.0.0.1:8000/docs`

---

### 3. Frontend Setup (React + Vite)

1. Open a new terminal and navigate to the frontend directory:
   ```bash
   cd Agriculture-ChatBot/frontend
   ```

2. Install dependencies:
   ```bash
   npm install --force
   ```

3. Start the local development server:
   ```bash
   npm run dev
   ```

- 🌐 **Web Application UI**: `http://localhost:3000`

---

### 🐳 Run with Docker Compose

If you have Docker installed, launch the entire application stack (MongoDB, Backend, and Frontend) in a single command:

```bash
cd Agriculture-ChatBot
docker-compose up --build
```

---

## ⚙️ Environment Variables

A template is provided in `.env.example`. Key configuration options include:

| Variable | Description | Default |
|:---|:---|:---|
| `MONGODB_URI` | MongoDB Atlas or local connection string | `mongodb://...` |
| `SECRET_KEY` | Application cryptographic secret | `super_secret_key` |
| `JWT_SECRET` | Secret key for JWT access token encoding | `jwt_secret_key` |
| `EMBEDDING_MODEL` | Hugging Face model for vector embeddings | `intfloat/multilingual-e5-base` |
| `ACTIVE_WEATHER_PROVIDER` | Weather data integration provider | `openweather` |
| `ACTIVE_MARKET_PROVIDER` | Mandi market price provider | `government` |
| `CORS_ORIGINS` | Allowed origins for cross-origin requests | `*` |

---

## 🧪 Verification & Health Checks

The backend includes automated verification scripts to validate platform modules:

```bash
cd Agriculture-ChatBot/backend
python verify_rag.py            # Validates RAG and vector retrieval
python verify_nlp.py            # Validates NLP entity and intent pipeline
python verify_ml.py             # Validates model registry benchmarking
python verify_plant_health.py   # Validates vision & OCR diagnostics
python verify_agri_services.py  # Validates weather and mandi data feeds
```

---

## 🛡️ Security & Best Practices

- **Authentication**: JWT-based stateless tokens with automatic refresh token rotation.
- **Rate Limiting**: Built-in request throttling middleware to protect backend resources.
- **Sanitization**: Strict input validation and sanitization via Pydantic v2 schemas.

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a descriptive feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add AmazingFeature'`).
4. Push to your branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
