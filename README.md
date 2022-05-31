# Caddy in a docker for my suksiboksi server setup

This repository contains configuration for getting Caddy running inside a docker container.

This particular setup reverse proxies into some of my services:

- Grafana: has duckdns.org provided DNS and Let's Encypt SSL certificate
- InfluxDB: uses localhost and path
- PiHole: uses local DNS

All the configuration to these services is handled by passing environment variables:

- docker-compose will read them from (e.g.) `.env` file
- docker-compose will pass them to Caddy and Caddyfile through its mechanism for managing environment variables (`environment` attribute)

Following variables are required for fully working setup:

```
GRAFANA_DUCKDNS_TOKEN=<YOUR_TOKEN>
GRAFANA_DUCKDNS_DOMAIN=<YOUR_DOMAIN; e.g. grafana.duckdns.org>
GRAFANA_TARGET_SERVICE=<YOUR_GRAFANA_TARGET_SERVICE; e.g. grafana:3000>
PIHOLE_DOMAIN=<YOUR_PIHOLE_DOMAIN; e.g. pi.hole>
PHIOLE_TARGET_SERVICE=<YOUR_PIHOLE_TARGET_SERVICE; e.g. pihole:8765>
INFLUXDB_TARGET_SERVICE=<YOUR_INFLUX_TARGET_SERVICE; e.g. influxdb:8086>
DOCKER_NETWORK=<YOUR_DOCKER_NETWORK; e.g. my_network>
EMAIL=<YOUR_EMAIL; e.g. somebody@example.com>
```
