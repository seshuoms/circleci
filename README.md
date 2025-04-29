# Spring Boot Hello World + Kubernetes (Minikube)

This project demonstrates a simple Spring Boot Hello World microservice deployed to a local Kubernetes cluster using Minikube.

## Prerequisites
- Docker
- Minikube
- Kubectl
- Maven

## Build & Run

### 1. Build the Spring Boot app
```bash
mvn clean package
```

### 2. Build Docker image inside Minikube
```bash
eval $(minikube docker-env)
docker build -t helloworld:latest .
```

### 3. Deploy to Kubernetes
```bash
kubectl apply -f k8s/helloworld-deployment.yaml
kubectl apply -f k8s/helloworld-service.yaml
```

### 4. Access the service
```bash
minikube service helloworld-service
```


## CI/CD with CircleCI (Local)

This project contains a CircleCI config file under `.circleci/config.yml`.

### To run CircleCI jobs locally:

1. Install CircleCI CLI:
```bash
brew install circleci
```
(Or on Windows)
```bash
choco install circleci-cli
```

2. Authenticate (dummy settings if local):
```bash
circleci setup
```

3. Run the build locally:
```bash
circleci local execute --job build
```

✅ This will build the project, Dockerize it, and deploy to your Minikube!
