# codex-lb Local Compose Setup

This folder has an image-based Compose setup matching the README quick start:

```bash
cd ~/codex-gateway
docker compose pull
docker compose up -d
```

Open the dashboard at http://localhost:2455, then add a ChatGPT account.

Useful commands:

```bash
docker compose logs -f codex-lb
docker compose ps
docker compose down
```

Hermes/OpenAI-compatible clients should use:

- Base URL: `http://127.0.0.1:2455/v1`
- Codex backend URL: `http://127.0.0.1:2455/backend-api/codex`

The dashboard is set to `CODEX_LB_DASHBOARD_AUTH_MODE=standard`. The README says API key auth is disabled by default, and only local protected proxy requests can proceed without a key. If Hermes agents run from another host, VM, or container network that codex-lb sees as non-local, enable API key auth in the dashboard under Settings -> API Key Auth, create a key, and configure Hermes to send it as `Authorization: Bearer sk-clb-...`.
