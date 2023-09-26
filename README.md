# 🤖 Policy Guru Chatbot 🏦

The Policy Insurance Chatbot is your virtual insurance assistant designed to make your insurance journey smooth and hassle-free! 😊

## Features ✨

- **24/7 Availability**: Our chatbot is always ready to assist you, day or night, weekdays or weekends. 🕰️

- **Policy Information**: Access your policy details, coverage information, and renewal dates with just a few clicks. 🔍📋

## How to Install 📝

Complete stand-alone application
```
docker compose up --build
```
## **System's Diagram** 

You can also take a look at the file `images/System_architecture_diagram.drawio.png` to have a graphical description of the microservices and how the communication is performed.

1. Create the database (Vector Database: Qdrant).
2. Check if the database is ready to upload information (Database Health-check).
3. Start ETL and then the database is ready.
4. Build frontend with Chainlit and the backend with FastAPI.
   
![System Diagram](images/System_architecture_diagram.drawio.png)

### Chainlit


Chainlit is an open-source Python package that makes it incredibly fast to build and share large language model (LLM) applications. It provides a ChatGPT-like user interface that allows developers to interact with their LLMs in a natural and intuitive way.

Chainlit has a number of key features that make it a valuable tool for LLM developers, including:

- Fast and easy development: Chainlit makes it possible to create LLM applications in minutes, even if you have no prior experience with web development.
- Visualize multi-steps reasoning: Chainlit can visualize the intermediary steps that produced an output, which can help developers to understand and debug their models.
- Element management and display: Chainlit provides a variety of UI elements that can be used to create rich and interactive applications.
- Cloud deployment: Chainlit applications can be deployed to the cloud with a single click.

Chainlit is still under development, but it is already being used by a number of companies and organizations to build innovative LLM applications. For example, Chainlit is being used to build:

- Chatbots: Chatbots that can provide customer support, generate creative content, and answer questions in an informative way.
- Code generation tools: Tools that can generate code in a variety of programming languages.
- Educational tools: Tools that can help students to learn new concepts and skills.
Chainlit is a powerful tool that can help developers to build and share LLM applications with ease. It is a valuable resource for anyone who is interested in using LLMs to solve real-world problems.

### Qdrant

Qdrant is a vector similarity search engine and vector database. It provides a production-ready service with a convenient API to store, search, and manage vectors with an additional payload.

Vectors are high-dimensional data representations that are often used to represent unstructured data, such as text, images, and audio. Vector similarity search algorithms can be used to find similar vectors in a large collection, which can be useful for a variety of tasks, such as:

- Recommendation systems: Qdrant can be used to build recommendation systems that suggest products, movies, or other items to users based on their past behavior.
- Image search: Qdrant can be used to build image search engines that allow users to find similar images to a given query image.
- Natural language processing (NLP): Qdrant can be used to build NLP applications that perform tasks such as text classification, sentiment analysis, and question answering.
Qdrant is a relatively new vector database, but it has quickly gained popularity due to its ease of use, performance, and scalability. It is also open source and freely available for use.

Here are some of the key features of Qdrant:

Production-ready: Qdrant is designed to be used in production environments. It is scalable and can handle large volumes of data.
Convenient API: Qdrant provides a convenient API for storing, searching, and managing vectors. The API is available in multiple languages, including Python, Java, and JavaScript.
Extended filtering support: Qdrant supports extended filtering of search results based on payload values. This makes it possible to create more sophisticated search applications.
Overall, Qdrant is a powerful and versatile vector database that can be used to build a wide variety of applications.

https://github.com/qdrant/qdrant

Don´t use ChromaDB because it's have a lot of bugs in deployment and updates daily.

## **Workflow**

![Workflow](images/workflow.png)

Code workflow:

1. The user sends a message to the chatbot.
2. The chatbot filters the question to remove any irrelevant information.
3. The chatbot creates a reasoning chain to determine how to answer the question.
4. The chatbot selects the tools that it needs to answer the question, such as a question embedding model, a language chain policy filtering model, and an OpenAI answer model.
5. The chatbot embeds the question using the question embedding model.
6. The chatbot uses the language chain policy filtering model to filter the embedded question.
7. The chatbot sends the filtered embedded question to the OpenAI answer model.
8. The OpenAI answer model generates an answer to the question.
9. The chatbot uses the language chain semantic search model to find similar chunks of text to the answer.
10. The chatbot creates a context for the answer using the similar chunks of text.
11. The chatbot sends the answer with the context to the user.

This workflow is designed to help the chatbot generate informative and comprehensive answers to the user's questions. The use of multiple tools and models allows the chatbot to better understand the question, find relevant information, and generate a high-quality answer.

Here is a more detailed explanation of each step:

**Step 1: Filter the question**

The chatbot first filters the question to remove any irrelevant information. This can help to improve the accuracy of the answer. For example, if the user asks "What is the capital of France?", the chatbot would remove the phrase "What is the capital of" from the question before processing it.

**Step 2: Create a reasoning chain**

The chatbot then creates a reasoning chain to determine how to answer the question. The reasoning chain is a sequence of steps that the chatbot will follow to generate the answer. For example, if the user asks "What is the best way to get to the airport?", the reasoning chain might be as follows:

Determine the user's current location.
Determine the user's desired arrival time at the airport.
Find the different transportation options available to the user.
Evaluate the different transportation options based on factors such as travel time, cost, and convenience.
Recommend the best transportation option to the user.

**Step 3: Select the tools**

The chatbot then selects the tools that it needs to answer the question. This might include a question embedding model, a language chain policy filtering model, and an OpenAI answer model.

**Step 4: Embed the question**

The chatbot then embeds the question using the question embedding model. The question embedding model converts the question into a high-dimensional vector representation. This vector representation captures the meaning of the question and can be used to find similar questions and answers in a large database.

**Step 5: Filter the embedded question**

The chatbot then uses the language chain policy filtering model to filter the embedded question. This model helps to ensure that the chatbot only generates answers that are relevant to the user's query.

**Step 6: Send the filtered embedded question to the OpenAI answer model**

The chatbot then sends the filtered embedded question to the OpenAI answer model. The OpenAI answer model is a large language model that can generate text, translate languages, write different kinds of creative content, and answer questions in an informative way.

**Step 7: Generate an answer**

The OpenAI answer model generates an answer to the question. The answer is a text string that provides information about the topic of the question.

**Step 8: Find similar chunks of text**

The chatbot then uses the language chain semantic search model to find similar chunks of text to the answer. This model helps to ensure that the chatbot provides comprehensive information about the topic of the question.

**Step 9: Create a context for the answer**

The chatbot then creates a context for the answer using the similar chunks of text. This context provides additional information about the topic of the question and helps the user to understand the answer better.

**Step 10: Send the answer with the context to the user**

The chatbot finally sends the answer with the context to the user. The user can then read the answer and learn more about the topic of their question.

This workflow is just one example of how a chatbot can be implemented. There are many other ways to design a chatbot, and the specific workflow will vary depending on the specific

## Folders architecture

```ut8
├── app
│   ├── agent_utils.py
│   ├── app.py
│   ├── chainlit.md
│   ├── config.py
│   ├── data_preloader
│   │   └── dataset
│   │       ├── raw_chunks
│   │       └── raw_pdfs
│   ├── data_utils.py
│   ├── Dockerfile
│   ├── __init__.py
│   ├── requirements.txt
│   └── text_templates.py
├── data_preloader
│   ├── config.py
│   ├── dataset
│   │   ├── raw_chunks
│   │   └── raw_pdfs
│   ├── data_utils.py
│   ├── Dockerfile
│   ├── document_utils.py
│   ├── health_check.py
│   ├── __init__.py
│   ├── main.py
│   ├── requirements.txt
│   └── text_preprocessing.py
├── dataset
│   ├── raw_chunks
│   └── raw_pdfs
├── docker-compose.yml
├── EDA.ipynb
├── env_template
├── images
├── LICENSE
├── qdrant_db
│   └── qdrant_storage
├── README.md
├── tests
    └── __init__.py

```


## Modules Documentation :gift:
Let's take a quick overview of each module:

### **app** :computer:

It has all the needed code to implement the front and backend of the chatbot. It uses Chainlit framework for LLMs.

- `app/agent_utils.py`: Includes the required function for the creation of a custom Agent Class and ChatBOT Class.
- `app/app.py`: Includes Chainlit front-end code
- `app/chainlit.md`: Markdown file for Chainlit README
- `app/config.py`: env variables for api configuration .
- `app/data_utils.py`: Includes Database connection and embbedgins loading.
- `app/text_templates.py`: Includes all the custom Prompt Templates.
- `feedback/feedback.txt`: Txt file to store reviews about answers.
- `chainlit.md`: Markdown file for Chainlit `README`
### **data_preloader** :floppy_disk:

Microservice forQdrant database initialization. 

-   `dataset/`: Predefined folder to store dowloaded and processed PDFs. This folder is shared with APP microservice in the `docker-compose.yml`: file to allow the user to download the PDFs.
-   `config.py`: env variables for api configuration .
- `data_utils.py` Functions to download the Data from S3.
- `document_utils.py` Preprocessing/Cleaning and Qdrant loading functions.
- `health_check.py` ENTRYPOINT for healtcheck microservice. Checks if Qdrant is ready to receive querys to avoid building errors.
- `main.py` ENTRYPOINT for preloader microservice. Downloads, procceses and saves the data in Qdrant.
- `text_preprocessing.py` Text normalization and preprocessing functions.

### **dataset** :newspaper:

Folder for data storage

- `raw_chunks`: Folder with the processed policies divived by policy number
- `raw_pdfs` Raw PDFS downloaded from S3

### **images** :sunny:

Key images for readme

### **qdrant_db** :mag_right:

Shared volume with Qdrant docker container. Saves all the embbegins information. Check the [documentation](https://qdrant.tech/).

### **stress_test** :fire:

Not related to the microservice architecture. Folder used to contain the locust fyle to test hardware performance.

- `locustfile.py` Contains `locust`` tests.


## Feedback 📢

We value your feedback and suggestions! If you have any ideas for improvement or encounter any issues, please let us know. 🙌📧

## Disclaimer 📜

The Policy Insurance Chatbot is designed to provide general insurance information and quotes. For specific policy details and personalized advice, we recommend consulting with our professional insurance agents. 👨‍💼🔍

Let's get started and simplify your insurance journey! 🚀💼


## Code Style


We use [Black](https://black.readthedocs.io/) and [isort](https://pycqa.github.io/isort/) for automated code formatting in this project, you can run it with:

```console
$ isort --profile=black . && black --line-length 88 .
```

Wanna read more about Python code style and good practices? Please see:
- [The Hitchhiker’s Guide to Python: Code Style](https://docs.python-guide.org/writing/style/)
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)
