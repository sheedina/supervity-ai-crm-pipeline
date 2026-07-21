# supervity-ai-crm-pipeline
A multi-agent AI orchestration pipeline built to automate sales lead triage, enforce dynamic business policies, and ensure strict data governance.
# 🚀 Inbound Revenue Capture AI Employee
**Supervity Autopilot Asia Hackathon Submission**

**Developers:** Gafar Aamir Mukhtar |Shee Rashid Dina, Computer Science, Albukhary International University (AIU)

### 🎬 Live Execution Demo
Watch the full end-to-end architecture and live execution in the demo video below:
🔗 https://drive.google.com/file/d/1X-hgW60Pv1Zt7GpKoqgAG0dB_NRvh0pj/view?usp=drivesdk

---

### ⚠️ The Problem
Sales organizations lose significant revenue due to the slow, manual triage of inbound leads. Furthermore, manually processing data often results in poor data governance, missed compliance checks, and unrecorded edge cases.

### 💡 The Solution
I architected a fully automated, multi-agent CRM pipeline using the Supervity platform. This **AI Employee** is designed to intake raw lead data, score it, enforce strict compliance policies, and loop in human operators only when necessary, accelerating response times and guaranteeing 100% auditability.

### ⚙️ System Architecture & Workflow
Instead of relying on a single fragile prompt, this system utilizes a **Main Orchestrator** to coordinate specialized sub-agents:

1. **Lead Intake & Enrichment (Dropbox):** The workflow is triggered by fetching raw lead payloads from secure cloud storage (Dropbox), ensuring enterprise-grade data intake. The Lead Enricher agent formats and cleans the data.
2. **AI Lead Scoring:** The enriched payload is passed to the AI Scorer, which evaluates the prospect and assigns a numerical value (1-100) using structured JSON schemas.
3. **Dynamic AI Policy Gates:** The system evaluates the data against a 3-tiered business logic gate:
   * **Low Score (<50):** Automatically approved and logged.
   * **High Score (>70):** Dynamically routed to trigger external multi-channel alerts.
   * **Risk Detection:** Suspicious email domains override standard routing for compliance.
4. **Live Integrations:** High-value leads instantly trigger a formatted alert in a designated **Slack** `#sales-leads` channel, and every single step is logged into a **Supabase** database for an immutable audit trail.
5. **Bonus Operator (Opportunity Alert):** A parallel extension that cross-references high-value leads to notify the sales team of immediate upsell potential.

### 🛡️ Exception Handling & Governance
To ensure production-readiness, robust human-in-the-loop exception handling was engineered into the pipeline.
* If the AI hallucinates (e.g., breaks the Pydantic schema).
* If the AI Policy detects a high-risk or suspicious lead.

The system does *not* crash or push bad data. It catches the exception and cleanly escalates the payload to the **Auto Workbench** for manual human review, ensuring zero compliance breaches.
