# Qdrant Vector Search with Reranking

A complete implementation of semantic search using Qdrant vector database and Cohere's embedding and reranking models. This notebook demonstrates how to build a high-quality retrieval system that combines vector similarity search with neural reranking for improved relevance.

## Features

- **Vector Database**: Qdrant for efficient similarity search
- **Embeddings**: Cohere's `embed-english-v3.0` for document and query encoding
- **Reranking**: Cohere's `rerank-english-v3.0` for relevance refinement
- **End-to-end Pipeline**: From document ingestion to ranked results

## Prerequisites

- Python 3.7+
- Google Colab (or local Jupyter environment)
- API keys for:
  - Qdrant Cloud
  - Cohere API

## Installation

```bash
pip install qdrant-client cohere
```

## Setup

1. **Get API Keys**:
   - Sign up for [Qdrant Cloud](https://cloud.qdrant.io/) and get your API key and cluster URL
   - Get your [Cohere API key](https://cohere.ai/)

2. **Configure Secrets** (in Google Colab):
   - Add `QDRANT_API_KEY` to Colab secrets
   - Add `QDRANT_URL` to Colab secrets  
   - Add `COHERE_API_KEY` to Colab secrets

## How It Works

### 1. Collection Creation
Creates a Qdrant collection with 1024-dimensional vectors using dot product similarity.

### 2. Document Embedding
- Sample documents about machine learning feature scaling
- Generates embeddings using Cohere's `embed-english-v3.0` model
- Stores documents with their vector representations in Qdrant

### 3. Query Processing
- Converts search queries to embeddings using the same model
- Performs vector similarity search to retrieve top candidates

### 4. Reranking
- Uses Cohere's `rerank-english-v3.0` to refine results
- Provides more accurate relevance scoring based on query-document interaction

## Usage

1. Open the notebook in Google Colab
2. Set up your API keys in Colab secrets
3. Run all cells sequentially
4. Modify the `query` variable to test different search queries

## Example Query

```python
query = "What is the purpose of feature scaling in machine learning?"
```

The system will:
1. Find semantically similar documents using vector search
2. Rerank results for better relevance
3. Return top 5 most relevant documents with scores

## Key Components

- **QdrantClient**: Manages vector database operations
- **Cohere Embed**: Generates high-quality text embeddings
- **Cohere Rerank**: Improves result relevance through cross-attention

## Benefits of This Approach

- **High Recall**: Vector search captures semantic similarity
- **High Precision**: Reranking improves relevance of top results
- **Scalable**: Qdrant handles large-scale vector operations efficiently
- **State-of-the-art**: Uses latest embedding and reranking models

## Customization

- **Documents**: Replace the sample documents with your own data
- **Collection Settings**: Adjust vector dimensions and distance metrics
- **Reranking**: Modify `top_n` parameter for different result counts
- **Models**: Experiment with different Cohere model versions

## Output Format

Results include:
- **Vector Search**: Document ID, similarity score, and content preview
- **Reranked Results**: Relevance score and reordered documents

## License

MIT License - feel free to use and modify for your projects.

## Contributing

Contributions welcome! Please feel free to submit issues and enhancement requests.
