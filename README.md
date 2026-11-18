# 🚀 DriftGuard – Automated MLOps Pipeline

An automated MLOps project that detects data drift, triggers machine learning model retraining, and exposes predictions through a FastAPI REST API. The application is containerized using Docker and published to Docker Hub.

## 📌 Project Overview

DriftGuard demonstrates an automated machine learning lifecycle using data drift detection and conditional model retraining.

The project uses the Iris classification dataset and a Random Forest classifier to predict flower categories based on four input features.

### Key Features

- **Machine Learning:** Iris classification using Random Forest.
- **REST API:** FastAPI-based prediction and health-check endpoints.
- **Data Drift Detection:** Statistical drift detection using the Kolmogorov-Smirnov (KS) Test.
- **Automated Retraining:** Retrains the model when data drift is detected.
- **Model Persistence:** Saves trained models using Joblib.
- **Containerization:** Docker-based application packaging.
- **Container Registry:** Docker Hub image publishing.
- **CI/CD Automation:** GitHub Actions workflow for automated drift checks, retraining and API testing.

## 🏗️ Project Architecture

```text
              Developer
                  |
                  v
             GitHub Repo
                  |
                  v
            GitHub Actions
                  |
                  v
         Data Drift Detection
                  |
             Drift Found?
              /       \
            Yes        No
             |          |
             v          |
        Model Retraining|
             |          |
             +----+-----+
                  |
                  v
             FastAPI Tests
                  |
                  v
              Docker Build
                  |
                  v
               Docker Hub
                  |
                  v
              Deployment
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| Scikit-learn | Machine learning |
| Random Forest | Classification algorithm |
| FastAPI | REST API development |
| NumPy | Numerical operations |
| SciPy | Statistical drift detection |
| Joblib | Model serialization |
| Uvicorn | ASGI server |
| Docker | Containerization |
| Docker Hub | Container image registry |
| Git & GitHub | Version control |
| GitHub Actions | CI/CD automation |

## 📂 Project Structure

```text
driftguard_mlops/
│
├── app.py
├── retrain.py
├── drift_monitor.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
├── .gitignore
├── model.pkl
│
└── .github/
    └── workflows/
        └── deploy.yml
```

## ⚙️ Local Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/shaunjohn-04/driftguard_mlops.git
```

### 2. Navigate to the project

```bash
cd driftguard_mlops
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the virtual environment

Windows:

```bash
venv\Scripts\activate
```

Linux:

```bash
source venv/bin/activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

## 🧠 Model Retraining

Execute the retraining script:

```bash
python retrain.py
```

The script trains a Random Forest classifier using the Iris dataset and saves the trained model as `model.pkl`.

## 📊 Data Drift Detection

Run the drift monitoring script:

```bash
python drift_monitor.py
```

The system compares reference data and current data using the Kolmogorov-Smirnov statistical test.

A p-value below 0.05 indicates statistically significant evidence of distribution drift.

## 🌐 Running the FastAPI Application

Start the API server:

```bash
uvicorn app:app --reload
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

### API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | API health check |
| POST | `/predict` | Iris flower prediction |

### Prediction Example

Request:

```json
{
  "features": [5.1, 3.5, 1.4, 0.2]
}
```

Response:

```json
{
  "model_version": "1.0.0",
  "prediction": 0
}
```

## 🐳 Docker Implementation

### Build Docker Image

```bash
docker build -t driftguard:v1 .
```

### Run Docker Container

```bash
docker run -d --name driftguard-container -p 8000:8000 driftguard:v1
```

### Verify Running Containers

```bash
docker ps
```

### Push Image to Docker Hub

Tag the image:

```bash
docker tag driftguard:v1 shaunjohnmathew/driftguard:v1
```

Push the image:

```bash
docker push shaunjohnmathew/driftguard:v1
```

### Docker Hub Repository

[DriftGuard – Docker Hub](https://hub.docker.com/r/shaunjohnmathew/driftguard)

## 🔄 CI/CD Pipeline

The GitHub Actions workflow is designed to automate the MLOps lifecycle:

1. Checkout source code.
2. Set up Python environment.
3. Install project dependencies.
4. Execute data drift detection.
5. Trigger model retraining when drift is detected.
6. Run API health and prediction tests.
7. Build and publish the Docker image.
8. Deploy the updated application.

**Note:** Docker Hub publishing and actual deployment are planned pipeline enhancements; the initial workflow still needs to be configured and validated.

## 🎯 Project Objectives

- Understand the machine learning lifecycle.
- Implement statistical data drift detection.
- Automate conditional model retraining.
- Expose ML predictions through REST APIs.
- Containerize machine learning applications.
- Integrate machine learning workflows with DevOps practices.

## 👨‍💻 Author

**Shaun John Mathew**

GitHub: [shaunjohn-04](https://github.com/shaunjohn-04)

---

⭐ If you find this project interesting, feel free to explore the repository!
