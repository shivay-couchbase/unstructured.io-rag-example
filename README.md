# Digital Library Assistant with Couchbase and Unstructured.io

This project showcases a **Digital Library Assistant** that leverages **Couchbase** for vector storage and retrieval, integrating various machine learning models for embedding and question-answering. The following guide outlines the steps to set up and run the project effectively.

## Create an Account on Unstructured.io

1. **Sign Up**: Create an account on [Unstructured.io](https://unstructured.io). Your free trial will commence upon registration.
2. **Obtain API Key**: Navigate to [API Keys](https://app.unstructured.io/keys) to retrieve your API key, which should be stored in the `.env` file.

## Prerequisites

- Python 3.8 or higher
- Couchbase
- Virtual environment (optional but recommended)
- Ollama/OpenAI

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd unstructured-couchbase-rag
   ```

2. **Create and Activate a Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Use `venv\Scripts\activate` on Windows
   ```

3. **Install Required Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Set Up Environment Variables**:
   Create a `.env` file in the `unstructured-couchbase-rag` directory with the following content:
   ```plaintext
   UNSTRUCTURED_API_KEY=get_your_key 
   UNSTRUCTURED_URL=https://api.unstructuredapp.io/general/v0/general
   EMBEDDING_MODEL=all-MiniLM-L6-v2
   CB_CONN_STR=""
   CB_USERNAME=""
   CB_PASSWORD=""
   CB_BUCKET=""
   CB_SCOPE=""
   CB_COLLECTION=""
   INDEX_NAME=""
   BOOKS_PATH="path/to/books"
   LOCAL_FILE_DOWNLOAD_DIR="local/path/to/download"
   ```

## Running the Project

### 1. ETL Process

The ETL (Extract, Transform, Load) process is managed by `books_etl.py`, which processes books and uploads them to Couchbase.

```bash
python books_etl.py
```
This process uses the Unstructured.io Destination connector (https://docs.unstructured.io/api-reference/ingest/destination-connector/couchbase) to import the local data files to Couchbase. 
This process will process the local files, and upload them to Couchbase with the generated embeddings. In this demo I am using Ollama Llama 3.1 model for RAG

### 2. Streamlit Application

Launch the main application, a Streamlit app that provides a user interface for interacting with the digital library assistant:

```bash
streamlit run streamlit_app.py
```

## Additional Information

- The `books` directory contains sample EPUB files for testing.
- Configuration files such as `index.json` and `mappings.json` are available for indexing and mappings setup.

## Conclusion

This setup allows you to harness the capabilities of Couchbase and Unstructured.io to create a powerful digital library assistant, enhancing data accessibility and interaction through advanced machine learning techniques.

Citations:
[1] https://unstructured.io
[2] https://www.langchain.com
[3] https://www.couchbase.com
