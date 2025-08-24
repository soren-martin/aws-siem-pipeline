# AWS → SIEM Detection Pipeline

A cloud log pipeline built in a homelab to practice detection engineering and cloud security monitoring.
Logs from **CloudTrail, GuardDuty, and VPC Flow Logs** are ingested into a SIEM (Elastic Cloud or Wazuh) for alerting and analysis.

---

## Architecture
![architecture](diagrams/architecture.png)

**Flow:**
1. AWS logs → S3
2. Kinesis Firehose / Lambda → SIEM
3. SIEM dashboards + detections
4. Alerts + playbooks

---

## Features
- Collection: CloudTrail, GuardDuty, VPC Flow Logs, IAM events
- 5 detection rules (IAM abuse, root login, MFA gaps, S3 exposure, GuardDuty findings)
- Dashboards: AWS event activity, GuardDuty severity trends, login geography
- Analyst playbooks: root login, policy changes, public S3

---

## Repo Structure
- `infra/` – scripts and Lambda for log forwarding
- `detections/` – detection rules in JSON/YAML
- `dashboards/` – exported SIEM dashboards
- `queries/` – sample Athena queries for log hunting
- `playbooks/` – Markdown incident response playbooks
- `docs/` – setup guide + lessons learned

---

## Getting Started
1. Clone repo
2. Enable CloudTrail, GuardDuty, VPC Flow Logs
3. Deploy Firehose/Lambda forwarder (see `/infra`)
4. Import detections & dashboards into SIEM
5. Generate test events (see `/docs/setup_steps.md`)

---

## Future Work
- Add AWS Config compliance rules
- Auto-remediation Lambda for public S3 buckets
- Honeypot log ingestion into same pipeline

---

## License
MIT License
