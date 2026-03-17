# Ansible Monitoring Automation

A comprehensive, production-ready Ansible suite to provision, configure, and integrate a complete monitoring stack, including Prometheus, Grafana, ELK (Elasticsearch, Kibana, Filebeat), Alertmanager, and Datadog.

## 🚀 Overview

This project provides 12 automated ways to set up and manage your infrastructure monitoring. It uses a modular role-based architecture, ensuring each component is independently manageable and scalable.

### Key Features
- **Infrastructure Metrics**: Automated `node_exporter` installation.
- **Dynamic Monitoring**: Prometheus with auto-discovery of inventory targets.
- **Visualization**: Grafana with automated datasource and dashboard provisioning.
- **Log Management**: Full ELK stack (Elasticsearch, Kibana, Filebeat) deployment.
- **Alerting**: Alertmanager with templated routing and receivers.
- **Cloud Integration**: Official Datadog agent integration.
- **Operational Excellence**: Support for rolling upgrades, health validation, and ILM policies.

## 📂 Project Structure

```text
ansible-monitoring-project/
├── group_vars/          # Global and group-specific variables
├── playbooks/           # Main and auxiliary playbooks
├── roles/               # Modular roles for each component
│   ├── alertmanager/
│   ├── datadog-agent/
│   ├── elk/
│   ├── grafana/
│   ├── node-exporter/
│   └── prometheus/
├── inventory.ini        # Infrastructure inventory
└── README.md           # Documentation
```

## 🛠️ Prerequisites

- **Ansible** installed on your control node.
- **Target Hosts** with SSH access.
- **Docker** installed on hosts running Prometheus, Grafana, and Alertmanager.
- **Sudo privileges** on target hosts.

## 🚀 Getting Started

### 1. Configure Inventory
Update `inventory.ini` with your server IP addresses or hostnames:
```ini
[exporters]
host1.example.com
host2.example.com

[prometheus]
prometheus-server.example.com

[grafana]
grafana-server.example.com
```

### 2. Set Variables
Edit `group_vars/all.yml` to specify desired versions and alert settings.

### 3. Deploy the Stack
Run the main playbook to provision everything:
```bash
ansible-playbook -i inventory.ini playbooks/site.yml
```

### 4. Validate Deployment
Verify that all services are healthy:
```bash
ansible-playbook -i inventory.ini playbooks/validate-monitoring.yml
```

## 🔧 Maintenance Operations

### Rolling Upgrades
Perform a zero-downtime rolling upgrade for Prometheus:
```bash
ansible-playbook -i inventory.ini playbooks/upgrade-prometheus.yml -e "prometheus_version=v2.48.0"
```

### Manage Log Indexing (ELK)
Bootstrap Elasticsearch Index Lifecycle Management (ILM):
```bash
ansible-playbook -i inventory.ini playbooks/elk-ilm.yml
```

## 🔒 Security Note
For production use, it is highly recommended to use **Ansible Vault** to encrypt sensitive data like API keys and passwords.

```bash
ansible-vault encrypt group_vars/secrets.yml
```

## 👤 Author
**Rajib Mahmud**
