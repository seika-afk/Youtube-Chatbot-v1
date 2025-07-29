# YouTube Chatbot (v1)

**Note:** This is version 1 of the project. A GUI and  updates will be introduced in future releases.

## Overview

This chatbot processes YouTube videos to provide answers to questions based on their transcripts. It integrates transcript extraction, semantic search, and LLM-based generation to deliver contextually accurate responses.

## Features

- Fetches English video transcripts using `youtube-transcript-api`
- Splits transcripts into overlapping chunks using LangChain
- Embeds text using `sentence-transformers/all-MiniLM-l6-v2`
- Stores embeddings using FAISS for efficient retrieval
- Uses a language model (DeepSeek-R1) to answer questions based on retrieved content

## How It Works

1. **Transcript Fetching**: Retrieves transcript of a given YouTube video using its ID.
2. **Chunking**: Splits long text into manageable overlapping parts for better embedding.
3. **Embedding & Indexing**: Chunks are embedded and stored in a FAISS vector store.
4. **Retrieval**: Relevant chunks are retrieved based on the user's question.
5. **Prompting**: The retrieved content is wrapped in a predefined prompt format.
6. **Answer Generation**: The prompt is passed to an LLM (via HuggingFace Inference API) to generate the answer.

## Installation

Install required dependencies:

```bash
pip install youtube-transcript-api langchain-community langchain-openai \
            faiss-cpu tiktoken python-dotenv
```

## Usage

1. Replace the `video_id` variable in the script with your desired YouTube video ID.
2. Set your HuggingFace API key in the appropriate line.
3. Run the script in your environment.
4. Type your question in the prompt when asked.
5. The chatbot will print a response generated using the video transcript.

## Planned Improvements

- GUI (desktop or web-based)
- Better exception handling and robustness
- Multi-language support
- Persistent vector database storage

---
