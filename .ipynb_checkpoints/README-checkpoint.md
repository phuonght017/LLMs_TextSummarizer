# Summarization Project

This project crawls website content and summarizes it using OpenAI's GPT-4o-mini model.

## 🚀 Setup Environment

### 1. Install Conda
If you haven't installed Conda, download and install it from [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or [Anaconda](https://www.anaconda.com/).

### 2. Create Conda Virtual Environment
```bash
conda env create -f environment.yml
conda activate llms
```

### 3. Install ChromeDriver
On macOS:
```bash
brew install chromedriver
```

On Ubuntu/Debian:
```bash
sudo apt update && sudo apt install -y chromium-chromedriver
```

On Windows:
1. Download ChromeDriver from [here](https://sites.google.com/chromium.org/driver/).
2. Extract and place `chromedriver.exe` in a directory included in your system's PATH.

## 📜 Web Summarization Code

### 1. `Website` Class (Crawling Data)
This class is responsible for fetching website content. Class `selenium` and `ChromeDriver` are used to crawl Javascript-rendered dynamic contents.

#### Example Usage:
```python
from website import Website

url = "https://example.com"
crawler = Website(url)
content = crawler.text
print(content)
```

### 2. Calling OpenAI API for Summarization
Function `summarize` calls OpenAI API for summarization

#### Code snippet:
```python
def summarize(url):
    website = Website(url)
    response = openai.chat.completions.create(
        model = "gpt-4o-mini",
        messages = messages_for(website)
    )
    return response.choices[0].message.content
```

## 📌 Notes
- Ensure your OpenAI API key is set in `.env` or as an environment variable.
- If crawling fails, check ChromeDriver installation and permissions.

## 📬 Contact
For any issues, please raise an issue in the repository or contact the maintainer.

