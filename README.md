# Linux Monitoring

Basic Linux monitoring stack using Prometheus and Grafana.

## Usage

```bash
docker compose up -d     # start
docker compose down      # stop (keep data)
docker compose down -v   # stop (reset everything)
```

## Components

### Prometheus 
Time-series database running on that scrapes and stores metrics from exporters

URL: http://localhost:9090

### Grafana
Visualization platform for building dashboards and exploring metrics

URL: http://localhost:3000 (admin / admin)

### Node Exporter
Exposes host system metrics (CPU, memory, disk, network)

URL: http://localhost:9100

## Run on boot (systemd)

Update the `WorkingDirectory` path, install the unit file and enable it:

```bash
sudo cp service/linux-monitoring.service /etc/systemd/system/linux-monitoring.service
sudo systemctl daemon-reload
sudo systemctl enable --now linux-monitoring.service
```

Troubleshooting:

```bash
systemctl status linux-monitoring.service
journalctl -u linux-monitoring.service -b
```
