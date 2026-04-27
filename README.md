# Container Testing — CHR30A Bitdefender Staging & Validation

Container staging and validation pipeline for deploying Bitdefender security agents on CHR30A home gateway hardware.

---

## Overview

This project validates the full container lifecycle for security agent deployment: build → stage → validate → promote to production.

---

## Pipeline

```
Build Container Image
        │
        ▼
Stage in Test Environment (CHR30A)
        │
        ▼
Run Validation Suite
  ├── Container integrity check (SHA256)
  ├── Service startup verification
  ├── Bitdefender agent registration
  ├── Network traffic inspection active
  └── DHS policy enforcement confirmed
        │
        ▼
Promote to Production  OR  Rollback
```

---

## Test Cases

| ID | Test | Expected Result |
|----|------|----------------|
| CT-001 | Container image integrity | SHA256 hash matches build artifact |
| CT-002 | Container startup time | < 30 seconds to ready state |
| CT-003 | Bitdefender agent registration | Agent visible in management console |
| CT-004 | Traffic inspection active | Packets analyzed, no bypass |
| CT-005 | Memory/CPU usage under load | Within hardware spec limits |
| CT-006 | Container restart recovery | State restored after restart |
| CT-007 | Firmware update compatibility | Container survives FW update cycle |
| CT-008 | Network isolation policy | Blocked traffic verified |

---

## Hardware Target

**CHR30A** — Verizon home gateway router
- Containerized Linux environment
- Bitdefender security agent deployment
- DHS (Device Host Security) policy layer

---

## Artifacts

- `CHR30A_Bitdefender_Container_Staging_&_Validation.mp4` — screen recording of full staging workflow
- Test result screenshots per sprint week
- Defect logs with reproduction steps

---

## Tools

```
Docker          — container build and runtime
Bitdefender     — security agent being validated
Python          — test automation scripts
Wireshark       — network traffic verification
Shell scripts   — CI/CD pipeline automation
```
