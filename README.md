# helm-webapp — Demo Chart for YouTube Tutorial

> **Helm Tutorial for Beginners 2026** — Demo project

## Quick Start

### Prerequisites
- Kubernetes cluster (minikube, kind, or cloud)
- kubectl configured
- Helm 3.x installed

### Install Helm
```bash
# macOS
brew install helm

# Linux
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Verify
helm version
```

### Deploy the Demo App

```bash
# Clone / download this repo
cd demo-chart

# Lint the chart (always do this first)
helm lint ./helm-webapp

# Preview what will be created (dry run)
helm install mywebapp ./helm-webapp --dry-run --debug

# Install with default values
helm install mywebapp ./helm-webapp

# Install for development
helm install mywebapp ./helm-webapp -f values/dev.yaml

# Install for production
helm install mywebapp ./helm-webapp -f values/prod.yaml

# Verify deployment
kubectl get pods
kubectl get svc
helm list
```

### Access the App (minikube)
```bash
minikube service mywebapp-helm-webapp
```

### Upgrade
```bash
helm upgrade mywebapp ./helm-webapp -f values/prod.yaml
helm history mywebapp
```

### Rollback
```bash
helm rollback mywebapp 1
```

### Run Helm Tests
```bash
helm test mywebapp
```

### Uninstall
```bash
helm uninstall mywebapp
```

## Chart Structure
```
helm-webapp/
├── Chart.yaml              # Chart metadata
├── values.yaml             # Default values
├── templates/
│   ├── _helpers.tpl        # Template helper functions
│   ├── deployment.yaml     # App deployment
│   ├── service.yaml        # Kubernetes service
│   ├── serviceaccount.yaml # Service account
│   ├── hpa.yaml            # Horizontal Pod Autoscaler
│   ├── ingress.yaml        # Ingress (optional)
│   ├── NOTES.txt           # Post-install instructions
│   └── tests/
│       └── test-connection.yaml  # Helm test
└── values/
    ├── dev.yaml    # Dev environment values
    └── prod.yaml   # Production values
```

## Key Commands Reference

| Command | Description |
|---------|-------------|
| `helm create <name>` | Scaffold a new chart |
| `helm lint ./chart` | Validate chart syntax |
| `helm template ./chart` | Render templates locally |
| `helm install <name> ./chart` | Install chart |
| `helm upgrade <name> ./chart` | Upgrade release |
| `helm upgrade --install <name> ./chart` | Install or upgrade (idempotent) |
| `helm rollback <name> <revision>` | Roll back to revision |
| `helm history <name>` | Show release history |
| `helm list` | List all releases |
| `helm uninstall <name>` | Remove release |
