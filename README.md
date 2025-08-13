# Wazuh---MISP-Integration
Wazuh &amp; MISP Integration for IoC 
# Wazuh ↔ MISP Integration Script

## Overview
This script enables integration between **Wazuh** (SIEM) and **MISP** (Malware Information Sharing Platform) to:
- Automatically extract **Indicators of Compromise (IoCs)** from Wazuh alerts.
- Query MISP using the `/attributes/restSearch` API.
- Append matched IoCs back into Wazuh events for correlation.
- Optionally save matched IP addresses into a local list for further actions (e.g., blocking).

---

## Features
- Secure TLS connection with optional CA bundle.
- Retry & timeout for API calls.
- POST request with filters to MISP `/attributes/restSearch`.
- Multiple match handling (returns more than one matched attribute).
- SHA-256 & IP validation (only global IPs are accepted).
- Safe file append with duplicate prevention.
- Robust JSON parsing for incomplete or custom alerts.
- English-only logs & comments for global team maintenance.

---

## Requirements
- Python 3.6+
- Wazuh Manager (running)
- MISP API key with read access
- `requests` Python library

---

## Installation

1. **Copy the script** to Wazuh integrations folder:
   ```bash
   cp misp_integration.py /var/ossec/integrations/
   chmod +x /var/ossec/integrations/misp_integration.py
