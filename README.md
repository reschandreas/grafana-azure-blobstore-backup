# grafana-backup

[![GHCR](https://img.shields.io/badge/ghcr.io-reschandreas%2Fgrafana--azure--blobstore--backup-blue?logo=github)](https://github.com/reschandreas/grafana-azure-blobstore-backup/pkgs/container/grafana-azure-blobstore-backup)

Container image with Azure CLI and gcx for Grafana 13+ dashboard operations.

## Contents

- **Azure CLI** - for Azure Blob Storage operations
- **gcx** - official Grafana CLI for dashboard export/import
- **jq** - JSON processing
- **bash** - scripting

## Build

```bash
docker build -t grafana-backup:latest .

# Multi-arch
docker buildx build --platform linux/amd64,linux/arm64 -t ghcr.io/reschandreas/grafana-azure-blobstore-backup:latest --push .
```

## Usage

```bash
docker run -it --rm \
  -e GRAFANA_URL=https://grafana.example.com \
  -e GRAFANA_TOKEN=glsa_xxx \
  grafana-backup:latest

# Inside container:
gcx resources list dashboards
az storage blob list --account-name xxx --container-name xxx
```

## Renovate

Configured for automatic updates of:
- Azure CLI base image
- gcx version

## Docker

```bash
docker pull ghcr.io/reschandreas/grafana-azure-blobstore-backup:latest
```
