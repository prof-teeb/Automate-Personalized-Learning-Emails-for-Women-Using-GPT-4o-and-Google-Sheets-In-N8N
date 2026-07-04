# 🎓 Automate Personalized Learning Emails for Women Using GPT-4o and Google Sheets

An enterprise-grade **n8n orchestration workflow** designed to scale personalized education programs for women. The system acts as an automated expert career coach and educator, pulling subscriber cohorts from **Google Sheets**, determining their individual learning milestones, pairing them with relevant topics, rewriting custom content utilizing **GPT-4o**, and delivering beautifully branded HTML emails via **Gmail**.

---

## 🛠️ How It Works

This workflow operates through a multi-stage automated data pipeline divided into three major functional zones[cite: 4]:

### 1. 📅 Cohort Ingestion & Phase Calculation
* **Daily Trigger:** Runs automatically every morning at 9:00 AM via a custom cron expression.
* **Subscriber Processing:** Fetches the entire directory of registered learners from the `Subscribers` sheet.
* **Dynamic Lifecycle Mapping:** Runs inline JavaScript to evaluate how many days a user has been active, bucketing them dynamically into tailored educational tiers (`Beginner`, `Intermediate`, or `Advanced`).

### 2. 🧠 Smart Content Matching & Hyper-Personalization
* **Matrix Matching Engine:** Cross-references each student's explicit `Topic Interest` and current learning `Phase` against a centralized `ContentLibrary` spreadsheet.
* **Batch Processing Loop:** Splits the matched cohort into single execution records to process distribution loops efficiently.
* **Generative Rewrite Engine:** Streams contextual criteria to **GPT-4o** to write a three-paragraph explanation adapted to their phase, an actionable 30-minute micro-task, key takeaways, and an inspiring motivational quote from a prominent woman leader in that specific industry.

### 3. 📧 Delivery & Analytics Logging
* **Branded Template Compilation:** Maps raw JSON payloads returned from the OpenAI engine into an inline CSS-styled, responsive, mobile-ready HTML newsletter layout.
* **Gmail Delivery:** Automatically routes the custom layout directly to the student's mailbox.
* **Immutable Logs:** Logs the full delivery metadata (`Date`, `Phase`, `Category`, `AI Snippet`, `Day Number`, `Subscriber Info`) back into a `SendLog` Google Sheet sheet for complete delivery auditing.

---

## 📋 Google Sheets Database Schema

To ensure the workflow executes flawlessly, structure your target Google Spreadsheet **"Women Skill Learning Automation"** with the following three worksheets[cite: 4]:

### 1. `Subscribers`
* Columns required: `Name`, `Email`, `Topic Interest`, `Subscribed Date`.

### 2. `ContentLibrary`
* Columns required: `Lesson Title`, `Category`, `Phase`, `Raw Content`, `Resource Link`.

### 3. `SendLog`
* Columns required: `Date`, `Phase`, `Category`, `AI Snippet`, `Day Number`, `Lesson Title`, `Subscriber Name`, `Subscriber Email`.

---
<img width="1473" height="372" alt="Automate Personalized Learning Emails for Women Using GPT-4o and Google Sheets" src="https://github.com/user-attachments/assets/26732328-da8d-4eae-81a0-11e0d0cbc2cc" />

---
## 🚀 Deployment & Setup Steps

1. **Import the Workflow:** Download the JSON file `RAG Workflow For Company Documents stored in Google Drive.json` from this repository, navigate to your n8n workspace canvas, click the top-right menu icon (`...`), and select **Import from File**.
2. **Setup Global Credentials:** 
   * **Google Sheets OAuth2:** Grant authorization to read your learner databases.
   * **OpenAI API Connection:** Provide a secret key to authenticate your `GPT-4o` prompts.
   * **Gmail OAuth2:** Connect your authorized distribution mailbox credentials.
3. **Map Spreadsheet IDs:** Ensure all three Google Sheet nodes point directly to the exact target spreadsheet ID hosting your data layout.
4. **Activate Automation:** Toggle the workspace canvas state from inactive to **Active** to begin automated tracking and scaling.

