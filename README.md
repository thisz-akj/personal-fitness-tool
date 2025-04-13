
# Personal Fitness Tool

**Personal Fitness Tool** is an intelligent fitness companion that helps users manage and track their fitness journey with AI-powered assistance. From personalized macro recommendations to notes and question answering, this tool leverages Langflow and AstraDB to build a full-stack, customizable experience.

---

##  Features

-  reate and manage user profiles with personal fitness goals
-  Dynamically update personal details and fitness goals
-  Add and delete personal fitness notes
-  Get AI-generated responses to health or fitness queries
-  Personalized macro calculation based on profile data
-  Modular prompt and flow system powered by Langflow
-  AstraDB-backed persistent storage

---

##  Tech Stack

| Technology       | Purpose                                  |
|------------------|------------------------------------------|
| **Python**       | Core application logic                   |
| **Streamlit**    | Interface + resource caching             |
| **Langflow**     | AI flow orchestration                    |
| **AstraDB (DataAPI)** | Cloud database for user data and notes |
| **.env**         | Securing API keys                        |

---

##  Project Structure

```bash
personal-fitness-tool/
│
├── ai.py                  # Langflow integration and AI prompt logic
├── main.py                # manages all the files and runs the frontend
├── db.py                  # AstraDB setup and collection access
├── form_submit.py         # Form handlers for updating profiles and notes
├── profile.py             # Profile creation and data fetch logic
│
├── flow/                  # Langflow JSON files
│   ├── AskAIV2.json
│   └── MacroFlow.json
│
├── prompts/               # Modular AI prompt templates
│   ├── macro.txt
│   ├── conditional_router.txt
│   ├── general_agent.txt
│   └── tool_calling_agent.txt
│
├── .env                   # API keys and environment variables
└── README.md              # Project documentation
```

---

## 🛠️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/thisz-akj/personal-fitness-tool.git
cd personal-fitness-tool
```

### 2. Install Requirements
```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a `.env` file and add the following:

```env
ASTRA_ENDPOINT=your_astra_db_endpoint
ASTRA_DB_APPLICATION_TOKEN=your_astra_token
LANGFLOW_TOKEN=your_langflow_api_token
```

---

##  Running the App

If integrated with Streamlit:

```bash
streamlit run app.py
```

> Make sure your app file (e.g. `app.py`) uses functions from `ai.py`, `profile.py`, etc.

---

## AI Prompt & Flow System

Prompts are stored in the `prompts/` folder and injected dynamically based on use-case:
- `macro.txt` – Macro calculation
- `tool_calling_agent.txt` – Smart reasoning
- `general_agent.txt` – General-purpose responses
- `conditional_router.txt` – Dynamic routing in flows

Langflow JSONs (`AskAIV2.json`, `MacroFlow.json`) are used with `run_flow_from_json()` and the Astra-hosted Langflow API.

---

##  Key Functions

### Profile Management
```python
create_profile(_id)
get_profile(_id)
update_personal_info(existing, update_type, **kwargs)
```

### Notes System
```python
add_note(note, profile_id)
delete_note(_id)
get_notes(_id)
```

### AI Interaction
```python
ask_ai(profile, question, agent_type="general_agent")
get_macros(profile, goals)
```

---

## Future Improvements

- Integrate wearable device data (Apple Watch, Fitbit)
- Visualize progress (charts, metrics)
- Community or trainer feedback integration
- Add advanced nutrition plans based on medical history

---

