# CI/CD Pipeline with GitHub Actions & Docker

![CI/CD Pipeline](https://github.com/yosrabnali/cicd-pipeline-project/actions/workflows/ci-cd.yml/badge.svg)

A production-ready CI/CD pipeline built with GitHub Actions and Docker.
Every code push automatically triggers testing and deployment to Docker Hub.

---

## Architecture
Developer → git push → GitHub Actions → Test → Build → Docker Hub

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python + Flask | Web application |
| Docker | Containerization |
| GitHub Actions | CI/CD automation |
| Docker Hub | Image registry |
| Pytest | Automated testing |

---

## Project Structure
cicd-pipeline-project/
├── app/
│   └── main.py                    # Flask application
├── tests/
│   └── test_main.py               # Automated tests
├── .github/
│   └── workflows/
│       └── ci-cd.yml              # CI/CD pipeline
├── Dockerfile                     # Container recipe
├── requirements.txt               # Python dependencies
└── README.md

---

## Pipeline Workflow

The pipeline runs automatically on every push to `main` :
git push
│
├── Job 1 : test
│     ├── Install Python 3.9
│     ├── Install dependencies
│     └── Run pytest → if fails : STOP
│
└── Job 2 : build (runs only if tests pass)
├── Login to Docker Hub
├── Build Docker image
└── Push image to Docker Hub

---

## API Endpoints

| Endpoint | Method | Response |
|----------|--------|----------|
| `/` | GET | `{"message": "...", "status": "healthy", "version": "1.0.0"}` |
| `/health` | GET | `{"status": "ok"}` |

---

## Getting Started

### Prerequisites

- Docker installed
- Git installed

### Run locally with Docker

```bash
# Pull the image from Docker Hub
docker pull yosrabenali/cicd-pipeline-project:latest

# Run the container
docker run -p 5000:5000 yosrabenali/cicd-pipeline-project:latest
```

Visit `http://localhost:5000` in your browser.

### Run locally without Docker

```bash
# Clone the repository
git clone https://github.com/yosrabnali/cicd-pipeline-project.git
cd cicd-pipeline-project

# Install dependencies
pip3 install -r requirements.txt

# Start the app
python3 -m flask --app app/main.py run
```

### Run tests

```bash
pytest tests/ -v
```

---

## CI/CD Setup

To use this pipeline in your own project :

1. Fork this repository
2. Create a Docker Hub account
3. Add these secrets in GitHub → Settings → Secrets :
   - `DOCKERHUB_USERNAME` : your Docker Hub username
   - `DOCKERHUB_TOKEN` : your Docker Hub access token
4. Push any change to `main` — the pipeline runs automatically

---

## What I Learned

- Building a REST API with Flask
- Writing automated tests with Pytest
- Containerizing an application with Docker
- Designing a CI/CD pipeline with GitHub Actions
- Managing credentials securely with GitHub Secrets
- Publishing Docker images to Docker Hub

---

## Author

**Yosra Benali**
Cloud & DevOps Engineer

[![GitHub](https://img.shields.io/badge/GitHub-yosrabnali-black)](https://github.com/yosrabnali)
[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-yosrabenali-blue)](https://hub.docker.com/r/yosrabenali)