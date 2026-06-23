# Document Intelligence with RAG

A document question-answering system built with Retrieval-Augmented Generation (RAG). Upload any PDF and ask questions in plain English. Answers are grounded only in the document, so the system doesn't make things up. If the answer isn't in the file, it says so.

**▶️ Try the live app:** https://huggingface.co/spaces/Sharonmary/document-intelligence-rag

This repo contains the notebook where I built the RAG pipeline step by step. The live app above runs the same logic with a web interface where anyone can upload their own PDF.

## What it does

Ask a document a question and get a grounded answer. Instead of keyword search, the system understands the meaning of your question, finds the most relevant passages, and writes an answer based only on those passages. A built-in guardrail makes it refuse questions the document doesn't cover, rather than inventing an answer.

## How it works

The notebook builds a four-step RAG pipeline:

1. **Chunk** — the document is split into overlapping passages
2. **Embed** — each passage becomes a vector capturing its meaning, using sentence-transformers
3. **Retrieve** — a question finds the most relevant passages by semantic similarity
4. **Generate** — those passages and the question go to Google's Gemini model, which writes a grounded answer

I tested it on Warren Buffett's 2023 shareholder letter and, in the live app, on Paytm's 2025 annual report. The guardrail was verified by asking a question outside the document (the capital of France), which it correctly declined to answer.

## Tools

Python, sentence-transformers (embeddings), Google Gemini (generation), pypdf (PDF reading), and Gradio for the deployed web app.

## A note on limitations

RAG can struggle with very large documents or data buried in tables, since tables lose structure when converted to plain text. Asking about narrative content (risks, strategy, policies) works best.

## Files

- `Document_Intelligence_RAG.ipynb` — the full pipeline, built and explained step by step

---

**About me:** I'm Sharonmary Lazer Baptist Anthony, building a data analytics portfolio focused on financial crime, fraud, and risk, and targeting data analyst roles where this kind of work matters.

Connect on [LinkedIn](https://www.linkedin.com/in/sharonmary-anthony-516078361).
