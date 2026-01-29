# testapp

Aplicacao exemplo em NestJS para uso com ArgoCD, registry local e runner self-hosted.

## Endpoints

- `GET /healthz` -> `OK`

## Requisitos

- Node.js 22
- pnpm

## Rodar localmente

```bash
pnpm install
pnpm run start:dev
```

Acesse: `http://localhost:3000/healthz`

## Build Docker

```bash
docker buildx build \
  --platform linux/arm64 \
  -t testapp:latest \
  -f docker/Dockerfile.testapp .
```

## Manifests Kubernetes

- `../testapp-manifests`: manifests da aplicacao
- `../cluster-manifests`: registry local e NodePort do app

## CI/CD (local)

Workflow em `.github/workflows/ci-cd-testapp.yml`:
- build/push no registry interno
- atualiza manifests
- sync no ArgoCD (opcional)
