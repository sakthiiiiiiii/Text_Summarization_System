# Legal & Compliance Text Summarization System

This repository contains an end-to-end legal and compliance text summarization system built in Python with Hugging Face Transformers. The project is implemented as a Jupyter notebook and focuses on generating concise, faithful summaries for long legal documents such as contracts, compliance notices, and policy text.

## Project Overview

The system uses a pretrained encoder-decoder model:
- Model: facebook/bart-large-cnn
- Approach: transfer learning with a pretrained summarization model
- No fine-tuning is performed, as the project is designed for inference-based summarization
- Handles long documents using sentence-aware chunking and a map-reduce summarization strategy

## Key Features

- Legal text preprocessing
- Subword tokenization using the BART tokenizer
- Handling long documents beyond the model token limit
- Chunk-based summarization for multi-page legal text
- Faithfulness-check heuristic for legal facts
- ROUGE-based evaluation of generated summaries
- Sample testing across short, medium, and long documents

## Repository Contents

- `Legal_Summarization_BART.ipynb` — full end-to-end summarization pipeline

## Objective

The goal is to summarize legal and compliance documents while preserving:
- important obligations
- dates and deadlines
- financial terms
- named parties and defined entities
- overall intent and meaning

This is especially useful in high-stakes legal settings where naive summarization may hallucinate critical details.

## Model and Method

The system:
1. Cleans and normalizes raw legal text
2. Splits long documents into sentence-aware chunks
3. Tokenizes text with the BART tokenizer
4. Summarizes each chunk
5. Combines chunk summaries
6. Re-summarizes if the combined output is still too long
7. Performs a faithfulness check against the source text
8. Computes ROUGE scores for evaluation

## Setup

This project is intended to run in:
- Google Colab
- Jupyter Notebook
- Python environment with required dependencies

Install dependencies:

```bash
pip install -q -U transformers datasets evaluate rouge_score nltk sentencepiece accelerate
```

## Usage

Open the notebook:
- `Legal_Summarization_BART.ipynb`

Then run all cells in order. The notebook includes:
- environment setup
- tokenizer loading
- model loading
- preprocessing
- chunking and summarization
- faithfulness checks
- ROUGE evaluation
- sample document testing

## Requirements

- Python 3.x
- Jupyter or Google Colab
- Hugging Face Transformers
- PyTorch
- Datasets
- Evaluate
- ROUGE score
- NLTK
- SentencePiece
- Accelerate

## Notes

- A GPU is recommended for faster inference, but CPU execution is also supported.
- The project uses a lightweight fact-grounding heuristic to flag unsupported amounts, dates, and named entities in generated summaries.
- ROUGE helps measure overlap with reference summaries, but it does not fully capture legal correctness; therefore, faithfulness checks are included.

## Potential Use Cases

- legal contract summaries
- compliance notice summaries
- policy document summarization
- contract clause abstraction
- risk and obligation extraction support

## License

This repository does not currently include a license file. Add an appropriate open-source license if you plan to share or distribute the project publicly.

## Contact / Repository

Repository:
https://github.com/sakthiiiiiiii/Text_Summarization_System
