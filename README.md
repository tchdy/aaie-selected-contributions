# AAIE — Selected Contributions: Synthetic Data for AI-Generated-Content Detection

> A write-up of my work on **AAIE (Artificial Assessment Intelligence for Educators)**, a team research capstone in Deakin University's **InnovAIte** program. AAIE builds LLM-powered tools that detect AI-assisted student work and generate rubric-aligned feedback for educators.
>
> The original repositories are private and owned by the project team. This repo summarizes **my individual contributions** and is shared with the team's permission. No private student data is included — all referenced data is synthetic.

---

## Why this is relevant to AI safety

Reliably distinguishing AI-generated from human-written text, and evaluating model outputs against explicit rubrics, are core problems in **model evaluation and oversight**. My work focused on building the **labeled, reproducible evaluation data** that detection and feedback models are tested against — the unglamorous-but-essential foundation that makes empirical claims about model behavior trustworthy. The project treated bias, reproducibility, and transparency as first-class requirements rather than afterthoughts.

---

## My role

**Data Curation & Generation pillar (aaie-Data-Hub).** I built and curated synthetic datasets that simulate how students use large language models to complete assignments, used downstream to train and evaluate the project's AI-detection and feedback-generation models.

Verified contributions (from my commit history) include:

- Authored **rubric-indexed dataset entries** for the Information Technology domain (e.g. `rub_it_0025`–`rub_it_0028`), each capturing an assignment prompt, a detailed rubric, simulated student–LLM question/answer chains, and graded final submissions across quality tiers.
- Generated **synthetic training samples** (student-style chat histories and final essays) via the OpenAI API.
- Produced **schema-validated JSON** conforming to the project's unified data schema, and corrected entries based on peer-review feedback.
- Worked through a disciplined **fork → branch → pull-request** workflow with peer and senior review.

---

## What the dataset captures

Each entry models a realistic AI-assisted submission so detection and feedback models can be evaluated on representative inputs:

| Field | Description |
|-------|-------------|
| `domain` | Academic field (e.g. Information Technology) |
| `prompt` | The assignment task given to students |
| `rubric` | Multi-criterion rubric with performance descriptors |
| `llm_questions` | Simulated student queries to an LLM |
| `llm_answers` | Corresponding LLM responses (the "AI assistance") |
| `final_submission` | A final, student-style essay (Excellent → Poor) |
| `feedback` | Evaluator feedback aligned to each rubric criterion |

This structure supports downstream tasks including **AI/Human/Hybrid classification**, **rubric-aligned feedback generation**, **submission-quality scoring**, and **prompt-chain reconstruction**.

---

## How it fed the wider project

The curated dataset was consumed by the project's **Model Lab**, which benchmarked open-source models (TinyLlama, Qwen, Mistral, and others) and commercial LLMs (GPT, Claude, Gemini) on detection and generation tasks using standard metrics — F1, AUC, precision/recall, BLEU, ROUGE — with explicit **bias, reproducibility, and transparency** checks.

---

## Ethics & safety

- **Fully synthetic.** No real student data is used; all prompts, chats, and submissions are generated or adapted.
- **Privacy-safe rubrics** curated or adapted to avoid exposing protected material.
- **Reproducibility-first**: schema validation and review gates on every contribution.

---

## Tech stack

`Python` · `OpenAI API` · `JSON Schema validation` · `Jupyter` · `Git` / `GitHub` (PR-based review)

Within the broader project: `PyTorch` · `HuggingFace Transformers` · `GitHub Actions CI/CD`

---

## Notes

- AAIE is a collaborative capstone; this document describes **my** contributions within a multi-pillar team and credits the project as joint work.
- Sample data and code excerpts can be added here on request, with any team-owned or sensitive material removed.

*Maintained by Isaac Onwuakaike — [github.com/tchdy](https://github.com/tchdy)*
