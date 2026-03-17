# AI API VS Code Assignment

A comprehensive learning project demonstrating how to work with AI APIs, prompt engineering, and large language models (LLMs) using Python.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Learning Topics](#learning-topics)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Project Overview

This project is designed as an educational assignment to learn and understand:
- How to interact with external APIs using Python
- Best practices for API client development
- Handling HTTP requests and responses
- Error handling and exception management
- Working with JSON data
- Understanding key AI concepts and terminology

The project includes a practical API client that demonstrates how to fetch data from a public API endpoint and process the responses appropriately.

## ✨ Features

- **API Client Module**: A robust client for making HTTP requests to external APIs
- **Utility Functions**: Helper functions for data formatting and processing
- **Sample Data Handling**: Examples of working with JSON responses
- **Error Handling**: Comprehensive error management for API calls
- **Educational Documentation**: Clear examples and comments for learning purposes
- **Modular Architecture**: Well-organized code structure for easy understanding and extension

## 📁 Project Structure

```
ai-api-vscode-assignment/
├── README.md                 # Project documentation (this file)
├── requirements.txt          # Python dependencies
├── ai-api-vscode-assignment.code-workspace  # VS Code workspace configuration
├── notes.txt                 # Additional notes and references
└── src/
    ├── __pycache__/         # Python bytecode cache
    ├── main.py              # Main application entry point
    ├── api_client.py        # API client implementation
    └── utils.py             # Utility functions for data processing
```

### File Descriptions

| File | Purpose |
|------|---------|
| `main.py` | Entry point for the application; orchestrates the workflow |
| `api_client.py` | Contains the `fetch_post()` function for making API calls |
| `utils.py` | Utility functions including `format_topic()` and `get_sample_topics()` |
| `requirements.txt` | Lists all Python package dependencies |

## 🚀 Installation

### Prerequisites

- Python 3.7 or higher
- pip (Python package manager)
- Virtual environment (recommended)

### Setup Steps

1. **Clone or navigate to the project directory**:
   ```bash
   cd /Users/hm/AI-Learning-master/ai-api-vscode-assignment
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python3 -m venv .venv
   ```

3. **Activate the virtual environment**:
   - macOS/Linux:
     ```bash
     source .venv/bin/activate
     ```
   - Windows:
     ```bash
     .venv\Scripts\activate
     ```

4. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## 📖 Usage

### Running the Application

To run the main application:

```bash
python src/main.py
```

### Expected Output

When you run the application, you should see:

```
Welcome to the AI API VS Code Assignment
--------------------------------------------------
Topics in this project:
Learning topic: Prompt Engineering
Learning topic: LLMs
Learning topic: Embeddings
Learning topic: AI APIs

Making a sample API call...
API Response:
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat...",
  "body": "quia et suscipit..."
}
```

### Using Individual Components

#### Fetching Data from API

```python
from src.api_client import fetch_post

# Fetch a post from the API
result = fetch_post()
print(result)
```

#### Using Utilities

```python
from src.utils import format_topic, get_sample_topics

# Get sample topics
topics = get_sample_topics()

# Format a topic for display
for topic in topics:
    print(format_topic(topic))
```

## 🔌 API Reference

### `api_client.py`

#### `fetch_post()`

Fetches a sample post from JSONPlaceholder API (a free fake REST API for testing).

**Function Signature:**
```python
def fetch_post() -> dict
```

**Returns:**
- `dict`: JSON response containing post data with keys:
  - `userId`: ID of the user who created the post
  - `id`: Post ID
  - `title`: Post title
  - `body`: Post content

**Example:**
```python
response = fetch_post()
if "error" in response:
    print(f"Error: {response['error']}")
else:
    print(f"Post Title: {response['title']}")
    print(f"Post Body: {response['body']}")
```

**Error Handling:**
- Returns a dictionary with `error` key if the request fails
- Handles network timeouts (10-second timeout)
- Catches all `requests.RequestException` errors

### `utils.py`

#### `get_sample_topics()`

Returns a list of AI learning topics covered in this project.

**Function Signature:**
```python
def get_sample_topics() -> list
```

**Returns:**
- `list`: List of topic strings
  - "Prompt Engineering"
  - "LLMs"
  - "Embeddings"
  - "AI APIs"

**Example:**
```python
topics = get_sample_topics()
print(f"Number of topics: {len(topics)}")
```

#### `format_topic(topic: str)`

Formats a topic string for display.

**Function Signature:**
```python
def format_topic(topic: str) -> str
```

**Parameters:**
- `topic` (str): The topic name to format

**Returns:**
- `str`: Formatted string in the format "Learning topic: {topic}"

**Example:**
```python
formatted = format_topic("AI APIs")
print(formatted)  # Output: Learning topic: AI APIs
```

## 📚 Learning Topics

This project covers the following AI and development concepts:

### 1. **Prompt Engineering**
   - Crafting effective prompts for AI models
   - Understanding how to interact with language models
   - Best practices for AI API communication

### 2. **Large Language Models (LLMs)**
   - Understanding how LLMs work
   - API-based vs. local model deployment
   - Common use cases and limitations

### 3. **Embeddings**
   - Converting text to vector representations
   - Using embeddings for similarity search
   - Embedding APIs and their applications

### 4. **AI APIs**
   - Making HTTP requests to AI services
   - Error handling and retry strategies
   - Rate limiting and best practices
   - Response parsing and data processing

## ⚙️ Configuration

### API Endpoints

The current implementation uses:
- **Base URL**: `https://jsonplaceholder.typicode.com`
- **Endpoint**: `/posts/1`

### Request Timeout

The API client is configured with a **10-second timeout** for all requests. You can modify this in `src/api_client.py`:

```python
response = requests.get(url, timeout=10)  # Change 10 to your desired timeout
```

### Dependencies

Current dependencies are listed in `requirements.txt`:
- `requests`: For making HTTP requests to external APIs

## 🐛 Troubleshooting

### Issue: `ModuleNotFoundError: No module named 'requests'`

**Solution**: Install the required dependencies:
```bash
pip install -r requirements.txt
```

### Issue: Network timeout errors

**Solution**: 
- Check your internet connection
- Verify the API endpoint is accessible
- Increase the timeout value in `api_client.py`

### Issue: Application doesn't start

**Solution**:
- Ensure the virtual environment is activated
- Check that you're running from the project root directory
- Verify Python version is 3.7 or higher: `python --version`

### Issue: JSON decoding errors

**Solution**: The API might be returning invalid JSON or the endpoint changed. Verify the API is still accessible by checking the URL in a browser.

## 🤝 Contributing

To extend this project:

1. **Add new API endpoints**: Create additional functions in `api_client.py`
2. **Add more utilities**: Expand `utils.py` with additional formatting or processing functions
3. **Add new learning topics**: Update `get_sample_topics()` to include new areas of study
4. **Improve error handling**: Add more specific exception handling for different error cases
5. **Add logging**: Implement logging for debugging and monitoring

## 📝 License

This is an educational assignment. Feel free to use and modify this code for learning purposes.

## 📞 Support

For issues or questions:
1. Check the Troubleshooting section above
2. Review the inline code comments in the source files
3. Consult the Learning Topics section for concept explanations
4. Check the notes.txt file for additional resources

---

**Last Updated**: March 2026
**Version**: 1.0.0
