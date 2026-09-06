# AI Resume Analyzer

A Streamlit application that analyzes resumes with AI. Upload a resume
(PDF, DOCX, or TXT), optionally add a job description, and get a structured,
honest feedback report — complete with a score, strengths, weak areas, missing
keywords, rewritten bullet points, and job-match analysis.

## Features

- **Multi-format resume upload** — reads text from PDF, DOCX, and TXT files.
- **Paste-text option** — analyze a resume without uploading a file.
- **Job-description matching** — optionally compare the resume against a role.
- **Structured AI report** — a 9-section analysis with an overall score out of 100.
- **Download the report** — save the analysis as a Markdown file.
- **Grounded feedback** — the AI is instructed to use only what's in the resume,
  never to invent experience or skills.

## Project structure

| File | Job |
|------|-----|
| `app.py` | The Streamlit user interface |
| `resume_service.py` | Extracts text from PDF, DOCX, and TXT files |
| `resume_prompts.py` | Builds the resume-analysis prompt |
| `llm_service.py` | The brain — routes messages to the chosen AI provider |
| `architecture_diagram.txt` | A visual map of how the app is structured |
| `.env` | Private settings + API key (never uploaded) |
| `.env.example` | Safe template showing which settings to create |

## Architecture

```
User uploads resume
      ↓
Text extraction        (resume_service.py)  → reads PDF / DOCX / TXT
      ↓
Prompt engineering     (resume_prompts.py)  → wraps text in instructions
      ↓
LLM service            (llm_service.py)      → sends to Gemini
      ↓
Report display + download  (app.py)
```

See `architecture_diagram.txt` for the full detailed diagram.

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Copy `.env.example` to `.env` and add your real key:
   ```bash
   cp .env.example .env
   ```
3. Run the app:
   ```bash
   streamlit run app.py
   ```

## Providers

- **Gemini** (default): free API key from Google AI Studio.
- **OpenAI**: OpenAI API key.
- **Ollama**: runs a model locally, no key needed.

Switch provider by editing `LLM_PROVIDER` in `.env`.

## Note

This is an educational resume-improvement tool, not an official hiring system.

---

Built by **Rana Refaat** as part of a personal AI engineering learning path.
