# Automated Visual UX Auditor

**An autonomous AI agent that visually audits web pages for design friction, accessibility issues, and conversion blockers using Claude 3.5 Sonnet.**

**Workflow:
**<img width="1090" height="410" alt="Screenshot 2025-12-05 at 12 18 23" src="https://github.com/user-attachments/assets/9f26eadf-b874-405d-a7ce-a9235514044f" />

**Sample output:
**<img width="1395" height="735" alt="Screenshot 2025-12-05 at 12 15 27" src="https://github.com/user-attachments/assets/a4d4076c-9f6a-47ea-ae30-c0376d06a4b5" />

## 🚀 Overview

Manual design QA and UX audits are time-consuming and subjective. This **n8n workflow** automates the heuristic analysis process by acting as an always-on "UX Auditor."

It iterates through a list of target URLs, captures high-resolution screenshots, and uses **Anthropic's Claude 3.5 Sonnet** (Visual LLM) to perform a deep-dive audit. The agent identifies layout shifts, confusing copy, low contrast, and friction points, then compiles a professional **Google Doc Report** for stakeholders.

**Perfect for:**
* **SaaS:** Auditing onboarding flows and dashboards.
* **eCommerce:** Checking checkout funnels and product pages.
* **Content:** Reviewing readability and layout on landing pages.
* **Agency:** Generating instant "Audit Reports" for prospective clients.

## ✨ Key Features

* **Multimodal AI Analysis:** Leverages **Claude 3.5 Sonnet** to "see" the interface like a human user, spotting visual inconsistencies that code-based linters miss.
* **Context-Aware:** The system can be prompted to act as different personas (e.g., "Accessibility Expert," "CRO Strategist," or "Brand Guardian").
* **Full-Loop Automation:** Handles the entire pipeline: `Input URLs` → `Visual Capture` → `AI Reasoning` → `Database Update` → `Report Generation`.
* **Professional Deliverables:** Automatically creates a structured Google Doc with executive summaries, severity ratings, and actionable fix recommendations.

## 🛠️ Tech Stack

* **Orchestration:** [n8n](https://n8n.io/)
* **Visual Intelligence:** Anthropic Claude 3.5 Sonnet
* **Tools:** ScreenshotAPI (or ScreenshotOne), Google Sheets, Google Docs

## 📄 Sample Output

The agent transforms raw URLs into a formatted audit report:

![Sample Report](sample_report.png)

## ⚙️ How It Works

1.  **Ingest:** The agent reads a batch of URLs from a Google Sheet (supporting specific viewports/devices).
2.  **Capture:** It visits each URL and captures a full-page or viewport screenshot, handling cookie banners and ads.
3.  **Analyze:** The image is sent to Claude 3.5 with a specific system prompt (e.g., *"Analyze this page for user friction and cognitive load..."*).
4.  **Report:**
    * Findings are logged row-by-row in Google Sheets.
    * Once the batch is complete, the agent compiles a consolidated **Executive Report** in Google Docs.

## 📦 Setup & Usage

### 1. Prerequisites
* An **n8n** instance (Cloud or Self-Hosted).
* **Anthropic API Key** (for Claude 3.5 Sonnet).
* **Google Cloud Console** project with Drive/Sheets/Docs APIs enabled.
* **Screenshot Service** API Key.

### 2. Installation
1.  **Clone/Download** this repository.
2.  **Import** `workflow.json` into n8n.
3.  **Configure Credentials** for the services listed above.

### 3. Usage
1.  Create a Google Sheet with headers: `URL`, `Analysis`.
2.  Add the URLs you want to audit.
3.  Run the workflow.
4.  Retrieve your finalized report from Google Drive.

## ⚠️ Customization

* **Change the Lens:** Edit the system prompt in the "Analyze Image" node to focus on different goals (e.g., *"Focus only on mobile responsiveness"* or *"Audit for WCAG accessibility compliance"*).
* **Adjust Output:** Modify the "Code Node" to change how the final report is formatted (e.g., adding Markdown tables or scores).

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

Built by **Shariq Iqbal: linkedin.com/in/shariqi**.
