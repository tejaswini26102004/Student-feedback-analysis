# AI-Powered Student Feedback Analyzer

---

## 🚀 Project Overview

This project delivers an **AI-powered web application** built with **Streamlit** to streamline the analysis of student feedback. It leverages advanced Natural Language Processing (NLP) models to automatically generate insightful summaries, classify sentiment, answer specific questions about individual responses, and provide an overall sentiment overview for the entire dataset. This tool empowers educators to quickly grasp student perceptions and identify key areas for improvement from qualitative data.

---

## ✨ Features

* **Individual Student Feedback Display:** Easily retrieve and view a student's complete raw feedback entries.
* **Automated Summarization:** Get a concise, AI-generated summary of each student's qualitative feedback.
* **Sentiment Analysis (Per Student):** Understand the overall emotional tone (Positive, Neutral, Negative) of an individual student's feedback.
* **Interactive Q&A:** Ask specific questions about a selected student's feedback (e.g., "What was their biggest challenge?") and receive direct, relevant answers.
* **Overall Dataset Sentiment Visualization:** Visualize the distribution of sentiment across all feedback entries in your dataset with a clear pie chart.
* **User-Friendly Interface:** An intuitive and interactive web dashboard, organized into distinct pages for seamless navigation.

---

## 🛠️ How It Works (Behind the Scenes)

This application is powered by a combination of Python libraries and pre-trained NLP models:

* **Data Handling:** Utilizes **Pandas** for efficient reading and processing of student feedback data from an Excel file (`.xlsx`).
* **Text Summarization:** Employs the **`sshleifer/distilbart-cnn-12-6`** model from **Hugging Face Transformers**. This model is fine-tuned for generating concise summaries of longer texts.
* **Sentiment Analysis:** Leverages the **`cardiffnlp/twitter-roberta-base-sentiment`** model, also from **Hugging Face Transformers**. This RoBERTa-based model is robust for classifying the sentiment of social media texts, making it suitable for short, qualitative feedback.
* **Rule-Based Q&A:** Implements a simple, keyword-matching logic to provide answers to common questions about feedback content.
* **Web Application Framework:** **Streamlit** is used to create the interactive, responsive, and easy-to-use web interface.
* **Visualization:** **Matplotlib** is integrated to generate insightful data visualizations, specifically the overall sentiment distribution pie chart.
* **Execution Environment:** Designed for seamless setup and deployment within a **Google Colab** environment, using `localtunnel` to provide a public URL for access.

---

## ⚙️ Setup & Running the Project (Google Colab)

Follow these steps to get the project running in your Google Colab environment:

1.  **Upload Your Data:**
    * Upload your Excel feedback file (e.g., `Feedback on Peer-to-Peer Teaching Methodology (1).xlsx`) directly to the root directory of your Colab environment (e.g., `/content/`).
    * **Note:** If your file has a different name, you will need to update the `file_path` variable in the `app.py` code.

2.  **Create `app.py`:**
    * In a Colab code cell, paste the entire `app.py` code (as provided in our conversation) and run the cell. Make sure the first line of the cell is `%%writefile app.py`. This command saves the code into a file named `app.py` in your Colab environment.

3.  **Install Dependencies:**
    * In a new Colab code cell, execute the following commands to install all required Python libraries and `localtunnel` (for public access):
        ```bash
        !pip install pandas openpyxl transformers streamlit matplotlib
        !npm install -g localtunnel
        ```

4.  **Launch the Streamlit App:**
    * In another new Colab code cell, run these commands to start the Streamlit application and generate a public URL:
        ```bash
        !nohup streamlit run app.py &

        import urllib
        print("Password/Enpoint IP for localtunnel is:",urllib.request.urlopen('[https://ipv4.icanhazip.com](https://ipv4.icanhazip.com)').read().decode('utf8').strip("\n"))
        !npx localtunnel --port 8501
        ```
    * A `localtunnel` URL (e.g., `https://xxxx-xxxx-xx.loca.lt`) will appear in the output. Click this link.
    * If prompted, enter the IP address displayed in your Colab output (e.g., `34.123.45.67`) into the localtunnel warning page.

---

## 🚀 Usage Guide

Once the Streamlit application loads in your browser:

1.  **Navigate Pages:** Use the sidebar on the left to switch between the "Student Feedback Analysis" page (for individual student insights and Q&A) and the "Overall Sentiment Visualization" page (for the dataset-wide chart).

2.  **Student Feedback Analysis Page:**
    * **Analyze Student:** Enter a **Student Name** in the text input box (e.g., "Afsheen Zaahrah A") and press Enter to see their summarized feedback, sentiment, and original responses.
    * **Ask Questions:** Once a student's feedback is loaded, use the **"Your Question"** input box to ask specific questions (e.g., "What was the biggest challenge?", "What did they like?", "What suggestions did they give?").
    * **Clear All:** Click the "Clear All" button to reset the inputs and analysis sections.

3.  **Overall Sentiment Visualization Page:**
    * Click the **"Generate Overall Sentiment Chart"** button to display a pie chart showing the distribution of Positive, Neutral, and Negative sentiments across all feedback entries in your dataset.

---

## 📊 Customizing for Your Own Dataset

This project is designed to be adaptable! To use it with a different Excel feedback file:

1.  **Update File Paths & Sheet Name:**
    * Modify the `file_path` and `sheet_name` variables in `app.py` to point to the exact location and name of your new Excel file and the relevant sheet within it.

2.  **Specify Student Name Column:**
    * Adjust the `student_name_column` variable in `app.py` to the **exact header name** of the column that contains student or participant names in your new dataset.

3.  **Crucially, Define `TEXT_FEEDBACK_COLUMNS`:**
    * The `TEXT_FEEDBACK_COLUMNS` list in `app.py` is essential. This list tells the application **which specific columns** in your Excel sheet contain the **qualitative text feedback** that the summarization and sentiment analysis models should process.
    * **You MUST update this list** to include the **precise column headers** (as they appear in your Excel file) for all the open-ended feedback questions. Make sure to exclude columns that are IDs, timestamps, numerical ratings, or any other data you don't want summarized or sentiment-analyzed.

    *Example (if your new Excel has columns like 'Question_1: What did you enjoy?' and 'Question_2: Areas for improvement?'):*
    ```python
    TEXT_FEEDBACK_COLUMNS = [
        'Question_1: What did you enjoy?',
        'Question_2: Areas for improvement?',
        # Add all other relevant qualitative feedback column names from your new dataset here
    ]
    ```

---

## 🛣️ Future Enhancements

* **Advanced Q&A Model:** Integrate a more sophisticated Question-Answering model (e.g., from Hugging Face's `question-answering` pipeline) for more nuanced and intelligent responses.
* **Topic Modeling:** Implement techniques like LDA or BERTopic to automatically identify key themes and recurring subjects within the feedback.
* **Interactive Filters:** Add interactive filters to the overall sentiment visualization (e.g., filter by course, demographic, or specific criteria).
* **Export Options:** Enable users to export generated summaries or analysis results (e.g., CSV, PDF).
* **User Authentication:** Implement user login for controlled access in multi-user environments.

---



