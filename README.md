
# Christ College Chatbot

This is a Rasa-powered chatbot designed for Christ College to provide information about the institute, its courses, location, contact details, and more.

## Project Structure

```
.
├── actions.py
├── config.yml
├── credentials.yml
├── data
│   ├── nlu.yml
│   ├── rules.yml
│   └── stories.yml
├── domain.yml
├── endpoints.yml
├── models
├── README.md
└── tests
    └── test_stories.yml
```

- `actions.py`: Contains custom actions for the bot.
- `config.yml`: Configuration for the Rasa pipeline and policies.
- `credentials.yml`: Credentials for connecting to messaging platforms.
- `data/nlu.yml`: Contains NLU training data.
- `data/rules.yml`: Contains rules for the bot's behavior.
- `data/stories.yml`: Contains training stories for the bot.
- `domain.yml`: Defines the bot's responses, intents, entities, slots, and actions.
- `endpoints.yml`: Configuration for connecting to custom actions.
- `models`: Directory where trained models are stored.
- `tests/test_stories.yml`: Test stories for verifying the bot's behavior.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Training the Model](#training-the-model)
- [Running the Bot](#running-the-bot)
- [Connecting to Telegram](#connecting-to-telegram)
- [License](#license)

## Features

- Provides information about Christ College.
- Lists various courses offered.
- Provides location, contact number.

## Installation

### Prerequisites

- Python 3.7+
- pip
- Virtual environment (venv)
- Git

### Steps

1. **Clone the repository:**

   ```

2. **Create and activate a virtual environment:**

   ```sh
   python3 -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. **Install Rasa:**

   ```sh
   pip install rasa
   ```

## Usage

1. **Initialize Rasa:**

   ```sh
   rasa init
   ```

2. **Train the Rasa model:**

   ```sh
   rasa train
   ```

3. **Make changes in the NLU, domain, and stories files:**

   - Edit `data/nlu.yml` for training examples.
   - Edit `domain.yml` for intents, responses, and actions.
   - Edit `data/stories.yml` for conversation flows.

4. **Connect to ngrok on port 5005:**

   ```sh
   ngrok http 5005
   ```

   Copy the HTTPS link provided by ngrok.

5. **Configure Telegram:**

   - Open `credentials.yml` and add your Telegram bot token and the ngrok HTTPS link.

   ```yml
   telegram:
     access_token: "YOUR_TELEGRAM_BOT_TOKEN"
     verify: "YOUR_TELEGRAM_BOT_NAME"
     webhook_url: "YOUR_NGROK_HTTPS_LINK/webhooks/telegram/webhook"
   ```

6. **Train the Rasa model again:**

   ```sh
   rasa train
   ```

## Running the Bot

1. **Run Rasa actions server:**

   ```sh
   rasa run actions
   ```

2. **Open a new terminal and run the Rasa server with API enabled and CORS support:**

   ```sh
   rasa run --enable-api --cors "*"
   ```

3. **Run the chatbot on localhost 5005:**

   ```sh
   rasa run -m models --enable-api --cors "*" --debug
   ```


## Intents and Responses

### Intents

- affirm
- bot_challenge
- deny
- goodbye
- greet
- location
- christ_course
- christ_intro
- mood_great
- mood_unhappy
- mathematics
- physics
- computerscience
- bba
- chemistry
- contact_number
- certifications
- first

### Responses

The bot provides various responses to user queries, including course details, contact information, and more.

## Example Conversations

**User:** Hi  
**Bot:** Hi, thank you for contacting Christ College. How can I help you?

**User:** Tell me about your courses  
**Bot:** We offer a variety of courses:  
- BSC Mathematics
- BSC Physics
- BSC Computer Science
- BBA
- BSC Chemistry 

**User:** Where is Christ College located?  
**Bot:** CHRIST COLLEGE (AUTONOMOUS) IRINJALAKUDA, IRINJALAKUDA, THRISSUR, KERALA, 680121, INDIA


## Custom Actions

Custom actions are implemented in `actions.py`. These actions can handle complex logic, integrate with external APIs, and provide dynamic responses.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

