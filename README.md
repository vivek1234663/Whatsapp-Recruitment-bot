# Whatsapp-Recruitment-bot
This project is an end-to-end AI-powered recruitment automation system built using n8n, WhatsApp Business API, and Google Sheets.

It enables automated job matching, candidate interaction, and screening through WhatsApp, significantly reducing manual recruiter workload.

📎 Workflow File:

🎯 Features
📱 WhatsApp-based job interaction system
🤖 Automated job matching from Google Sheets
🔘 Interactive buttons (Interested / Show More / Next Job)
📊 Candidate tracking and logging
🧠 Automated qualification screening
📝 Multi-step question-based filtering system
⚡ Real-time API-based communication
🧩 Tech Stack
Automation: n8n
Messaging: WhatsApp Business API (Meta Graph API)
Database: Google Sheets
Backend Logic: JavaScript (inside n8n nodes)
APIs: REST APIs, Webhooks
⚙️ Workflow Overview
1️⃣ Incoming Message Handling
User sends a message via WhatsApp
Webhook (WhatsApp Message Received) triggers the workflow
Extracts:
Phone Number
Message Text
Timestamp
2️⃣ Job Matching
Fetches job data from Google Sheets
Checks if jobs are available
👉 If NO jobs:

Sends message:

"No job opportunities available"

👉 If jobs exist:
Prepares job data
Sends interactive job card with buttons:
Interested
Show More
Next Job
3️⃣ User Interaction Handling

User responses are captured via webhook:

🔘 Interested
Logs interest in Google Sheets
Starts qualification process
🔘 Show More
Fetches full job details
Sends:
Job description
Benefits
Logs interaction
🔘 Next Job
Fetches next available job
Sends new job offer
If no more jobs → sends fallback message
4️⃣ Qualification Flow
Fetches screening questions from Google Sheets
Sends questions one-by-one using buttons:
Yes
No
5️⃣ Answer Processing
Captures answers via webhook
Stores responses in Google Sheets
Checks:
More questions remaining?
6️⃣ Final Evaluation
Calculates qualification status:
✅ Qualified
❌ Not Qualified
7️⃣ Final Output
✅ If Qualified:

Sends:

"Congratulations! You are qualified"

❌ If Not Qualified:

Sends:

"You do not meet requirements"

📊 Google Sheets Structure
Jobs Sheet
job_id
employer_name
job_intro
job_description
job_benefits
Questions Sheet
question_id
question_text
Candidates Sheet
phone_number
responses
qualification_status
🔄 Workflow Architecture
WhatsApp → Webhook → n8n Workflow
        → Google Sheets (Jobs/Questions)
        → Decision Logic
        → WhatsApp Response
🔐 Setup Instructions
1. Requirements
n8n (Cloud / Self-hosted)
WhatsApp Business API (Meta)
Google Sheets API Credentials
2. Steps
Step 1: Import Workflow
Import JSON file into n8n
Step 2: Configure Credentials
Meta API Token
Google Sheets OAuth
Step 3: Update Webhooks
/whatsapp-webhook
/whatsapp-response
/whatsapp-answer
3. Replace Placeholders

Update:

<phone_number_id>
Meta Access Token
Google Sheet IDs
