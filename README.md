# 📄 CV Screening Automation with n8n

An automated CV screening workflow built with **n8n** that extracts text from PDF resumes, matches candidate skills against job requirements, calculates a screening score, and generates preliminary results for manual review.

## 🚀 Features

- 📤 **CV Upload:** Receive PDF resumes through an n8n Webhook.
- 📝 **Text Extraction:** Extract text from uploaded PDF files.
- 🔍 **Skill Matching:** Compare candidate skills with required and preferred job skills.
- 📊 **Screening Score:** Calculate a score out of 100 based on keyword matches.
- ✅ **Preliminary Classification:** Identify potential matches for further review.
- 📋 **Detailed Results:** Display matched skills, missing required keywords, and an extracted text preview.
- ⚙️ **Customizable Criteria:** Modify the job title and required skills in the Code node.

## 🛠️ Technologies Used

- **n8n** — Workflow automation
- **JavaScript** — CV screening and scoring logic
- **Webhook** — Receive CV uploads
- **PDF Text Extraction** — Extract resume content
- **JSON** — Workflow configuration and import/export

## 🔄 Workflow

1. **Upload CV:** The Webhook receives a PDF resume.
2. **Extract PDF Text:** The Extract From File node extracts the resume text.
3. **Screen CV:** The Code node matches extracted text against job criteria.
4. **Generate Results:** The workflow returns a score, matched skills, missing keywords, and a preliminary review category.

## 📂 Project Structure

```text
n8n-cv-screening-automation/
│
├── cv_screening_automation_n8n.json
└── README.md
```

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/smattah420/n8n-cv-screening-automation.git
cd n8n-cv-screening-automation
```

### 2. Import the workflow into n8n

1. Open your n8n workspace.
2. Open the workflow menu.
3. Select **Import from File**.
4. Choose `cv_screening_automation_n8n.json`.

### 3. Configure job requirements

Open the **Screen CV Against Job Criteria** Code node and customize the job title, required skills, preferred skills, and minimum required matches.

### 4. Test the workflow

1. Open the **Upload CV (Webhook)** node.
2. Start listening for a test event.
3. Send a PDF file using a multipart/form-data request with the binary field name `data`.
4. Check the output of the screening node.

Example using `curl`:

```bash
curl -X POST "YOUR_N8N_TEST_WEBHOOK_URL" \
  -F "data=@resume.pdf"
```

Replace `YOUR_N8N_TEST_WEBHOOK_URL` with the Test URL shown in your Webhook node.

## 📊 Example Output

```json
{
  "jobTitle": "Full Stack Developer",
  "screeningMethod": "Keyword matching only; not an employment decision",
  "scoreOutOf100": 72,
  "preliminaryCategory": "Potential match - review CV",
  "matchedRequiredSkills": [
    "javascript",
    "react",
    "mongodb",
    "git"
  ],
  "matchedPreferredSkills": [
    "python",
    "django"
  ],
  "missingRequiredSkills": [
    "node.js",
    "express",
    "api"
  ],
  "note": "Verify skills and experience manually."
}
```

*The output above is illustrative; actual results depend on the uploaded CV and configured criteria.*

## 🎯 Use Cases

- Recruitment workflow automation
- Initial resume screening
- Technical skill keyword matching
- HR process improvement
- Learning and practicing n8n automation

## ⚠️ Limitations

- The starter workflow processes PDF resumes only.
- Screening is based on keyword matching, not advanced AI understanding.
- The score represents keyword coverage, not a candidate's actual competence.
- Missing keywords do not necessarily mean a candidate lacks a skill.
- The workflow does not currently save candidate records to a database or send email notifications.

**Important:** Use the results only as decision-support information. A human recruiter should review each CV and make hiring decisions fairly. Avoid using protected or sensitive personal characteristics in screening criteria.

## 🔮 Future Improvements

- Integrate an AI model for contextual CV analysis.
- Store candidate information and screening results in PostgreSQL.
- Send notifications using Gmail.
- Support DOCX resumes.
- Generate candidate comparison reports.
- Add a job description input form.

## 👨‍💻 Author

**Syed Md Attah ur Rehman**

Software Engineering Undergraduate | Full-Stack Developer | Python Developer

- GitHub: [@smattah420](https://github.com/smattah420)

## 📜 License

This project is available for learning and personal portfolio use. Add a formal open-source license if you intend to specify permissions for reuse and distribution.

