# PDF Chatbot with LangChain and Google AI

A Streamlit-based chatbot application that allows users to upload PDF documents and ask questions to get AI-powered answers based on the content. Built using LangChain, Google's Generative AI, and FAISS for efficient vector search.

## Features

- **PDF Text Extraction**: Extract text from multiple PDF files
- **Intelligent Chunking**: Split large documents into manageable chunks with overlap
- **Vector Embeddings**: Create semantic embeddings using Google's embedding models
- **Fast Retrieval**: Use FAISS vector database for quick similarity search
- **Conversational AI**: Answer questions using Google's Gemini Pro model
- **Context-Aware Responses**: Distinguishes between document-based and general knowledge answers
- **Web Interface**: Clean Streamlit UI for easy interaction

## Prerequisites

- Python 3.10 or higher
- Google Cloud API key with Generative AI access
- Virtual environment (already set up in `env/`)

## Installation

1. **Clone the repository** (if not already done):
   ```bash
   git clone https://github.com/usamullah/specific-PDF-chat-bot-.git
   cd specific-PDF-chat-bot-
   ```

2. **Activate the virtual environment**:
   ```bash
   # On Windows
   .\env\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Environment Setup

1. Create a `.env` file in the root directory:
   ```
   GOOGLE_API_KEY=your_google_api_key_here
   ```

2. Get your Google API key from [Google AI Studio](https://makersuite.google.com/app/apikey)

## Usage

1. **Run the application**:
   ```bash
   streamlit run app.py
   ```

2. **Open your browser** to the URL shown (typically http://localhost:8501)

3. **Upload PDF files** using the sidebar uploader

4. **Ask questions** in the text input field

5. **Click "Process and Answer"** to get responses

## Project Structure

```
├── app.py                 # Main Streamlit application
├── apikey_test.py         # API key verification script
├── requirements.txt       # Python dependencies
├── README.md             # This file
├── .env                  # Environment variables (create this)
├── faiss_index/          # Vector database storage
│   └── index.faiss       # FAISS index file
└── env/                  # Virtual environment
```

## How It Works

1. **Text Extraction**: PDFs are processed using PyPDF2 to extract raw text
2. **Text Splitting**: Documents are divided into chunks of 10,000 characters with 1,000 character overlap
3. **Embedding Creation**: Each chunk is converted to vector embeddings using Google's `models/embedding-001`
4. **Vector Storage**: Embeddings are stored in a FAISS index for efficient retrieval
5. **Question Processing**: User questions are embedded and matched against document chunks
6. **Answer Generation**: Relevant chunks are fed to Google's Gemini Pro model with a custom prompt

## API Key Testing

To verify your API key is set correctly:

```bash
python apikey_test.py
```

## Dependencies

Key libraries used:
- `streamlit`: Web application framework
- `langchain`: LLM orchestration framework
- `google-generativeai`: Google's AI models
- `faiss-cpu`: Vector similarity search
- `PyPDF2`: PDF text extraction
- `python-dotenv`: Environment variable management

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source. Please check the license file for details.

## Troubleshooting

- **API Key Issues**: Ensure your `.env` file exists and contains a valid Google API key
- **PDF Processing Errors**: Make sure uploaded PDFs contain extractable text
- **Memory Issues**: For very large PDFs, consider increasing chunk overlap or reducing chunk size
- **Streamlit Errors**: Ensure all dependencies are installed and virtual environment is activated

## Future Enhancements

- Support for more document formats (DOCX, TXT, etc.)
- Conversation history and context retention
- Multiple language support
- Batch processing capabilities
- Cloud deployment options 
