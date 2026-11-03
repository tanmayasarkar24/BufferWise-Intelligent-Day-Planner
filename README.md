# BufferWise-Intelligent-Day-Planner
BufferWise is intelligent day planner that helps organise meetings, resolve schedule conflicts, estimate travel time, and add practical buffers for preparation and breaks. Built with Python, Pandas, and Gradio, it demonstrates rule-based scheduling, BDI reasoning, agent coordination, optional weather adjustments, and message-integrity verification.


## 📌 About the Project

Traditional calendar applications mainly focus on meeting start and end times. However, real-life scheduling involves more than just managing time slots. People also need time to travel between locations, prepare for important meetings, and take breaks.

**BufferWise** addresses these challenges through an intelligent scheduling agent that analyses calendar events, identifies scheduling conflicts, estimates travel requirements, and adjusts meeting schedules using predefined decision-making rules.

The project also demonstrates agent coordination through utility-based meeting-slot selection and message integrity verification using HMAC-SHA256.

## 🎯 Project Objectives

- Organise daily meetings into a chronological schedule.
- Detect and resolve overlapping meetings.
- Estimate travel time between consecutive meeting locations.
- Account for travel safety buffers.
- Provide additional preparation time for high-stakes meetings.
- Identify tightly scheduled meetings and consider break requirements.
- Demonstrate intelligent decision-making using the BDI model.
- Provide an explanation of the agent's scheduling decisions.
- Demonstrate coordination and message-integrity concepts.

## ✨ Key Features

### 1. Intelligent Meeting Scheduling
- Accepts meeting details through an interactive interface.
- Validates meeting timings and travel information.
- Sorts meetings chronologically.
- Detects overlapping meetings.
- Adjusts meeting timings based on scheduling rules.

### 2. Travel-Time Estimation

Estimates travel duration using distance and assumed average speed.

**Formula:**

Travel Time (minutes) = (Distance in km / Average Speed in km/h) × 60

Assumed average speeds:

| Travel Mode | Average Speed |
|---|---:|
| Car | 30 km/h |
| Bike | 25 km/h |
| Public Transport | 20 km/h |

The system also supports manually entered travel durations and traffic multipliers.

### 3. Buffer Management
- Travel safety buffers between meetings.
- Preparation buffers for high-stakes meetings.
- Additional break requirements for tightly packed schedules.
- Optional weather-based adjustments.

### 4. Weather-Based Adjustment

Uses the Open-Meteo API to retrieve weather information when live weather is enabled.

Weather conditions can influence estimated travel time and additional buffer requirements.

If live weather is disabled or unavailable, the system uses baseline weather settings.

### 5. BDI-Based Decision Representation

The scheduling agent represents its decision-making using the BDI model:

| Component | Description |
|---|---|
| Beliefs | Information known to the agent, such as meetings, locations, traffic and weather |
| Desires | Goals such as arriving on time and maintaining a practical schedule |
| Intentions | Planned actions such as checking gaps, estimating travel and adjusting meetings |

A decision trace is generated to explain the scheduling actions.

### 6. Meeting-Slot Coordination Demonstration

Demonstrates utility-based coordination between two simulated participants, Alice and Bob.

- Each participant has a preferred meeting time.
- Candidate time slots are evaluated using utility scores.
- The average utility is calculated.
- The slot with the highest average utility is selected.

This is a simplified utility-based demonstration, not the complete alternating-offer negotiation protocol.

### 7. Message Integrity Demonstration

Demonstrates message signing and verification using HMAC-SHA256.

- Generates a signature using a shared secret key.
- Verifies the original message.
- Modifies the message payload.
- Detects the modification through signature verification.

The current UI demonstrates local signing and verification. Full TCP communication and replay-protection checks are separate assignment implementations.

## 🏗️ System Architecture

The project consists of the following modules:

1. **User Input Module** – Receives calendar details, meeting timings, locations and travel preferences.
2. **Scheduling Agent** – Processes meetings and manages scheduling decisions.
3. **Decision-Making Module** – Applies predefined rules and represents the BDI model.
4. **Travel Estimation Module** – Calculates travel requirements using distance, average speed and traffic adjustments.
5. **Weather Module** – Provides optional weather-based adjustments.
6. **Output Module** – Displays the updated schedule, summary and decision trace.
7. **Coordination Module** – Demonstrates utility-based meeting-slot selection.
8. **Trust Module** – Demonstrates HMAC-SHA256 message integrity verification.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Google Colab | Development and execution environment |
| Gradio | Interactive web interface |
| Pandas | Calendar data processing |
| Requests | Weather API communication |
| Open-Meteo API | Weather information |
| JSON | Structured message representation |
| HMAC-SHA256 | Message integrity verification |

## ⚙️ Installation and Setup

### Prerequisites

- Python 3.9 or later
- Google Colab or a local Python environment
- Internet connection for package installation and optional weather access

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/BufferWise.git
```

### 2. Navigate to the Project Directory

```bash
cd BufferWise
```

### 3. Install Dependencies

```bash
pip install gradio pandas requests
```

### 4. Run the Project

If the project is provided as a Google Colab notebook:

1. Open the `.ipynb` notebook in Google Colab.
2. Install the required libraries.
3. Run the notebook cells in order.
4. Execute the final Gradio launch cell.
5. Open the generated Gradio link to interact with BufferWise.

For local execution, run the notebook using Jupyter Notebook or JupyterLab.

## 🚀 How to Use

1. Open the BufferWise application.
2. Enter meeting details in the calendar table or use the sample schedule.
3. Select the preferred travel mode.
4. Set the travel safety buffer.
5. Choose Automatic or Manual traffic adjustment.
6. Enter the city if live weather information is required.
7. Enable live weather if desired.
8. Click **Run BufferWise**.
9. View the updated schedule and planning summary.
10. Open the Agent's Reasoning tab to understand the decisions.
11. Explore the Coordination & Trust tab to run the supporting demonstrations.

## 📊 Example Input

| Meeting | Start | End | Location |
|---|---|---|---|
| Team Standup | 09:00 | 09:30 | Office |
| Client Presentation | 09:40 | 10:30 | Downtown |
| Manager Meeting | 10:50 | 11:35 | Office |
| Budget Review | 11:40 | 12:20 | Office |

Additional travel information can be provided through the distance and manual travel-time columns.

## 📁 Project Structure

A suggested repository structure:

```text
BufferWise/
│
├── BufferWise.ipynb
├── README.md
├── requirements.txt
└── assets/
    ├── architecture.png
    └── interface.png
```

*The structure above is a suggested organisation. Include only the files and screenshots that are actually present in your repository.*

## 🔍 Project Limitations

- Travel estimates use assumed average speeds and manually provided distances, not live map routing.
- Automatic traffic adjustment uses a predefined multiplier rather than real-time traffic monitoring.
- Weather adjustments depend on the availability of the external weather API.
- The current negotiation interface demonstrates simplified utility-based slot comparison.
- The current security interface demonstrates local HMAC signing and verification.
- Full TCP socket communication, complete negotiation protocols and replay-protection mechanisms are separate assignment implementations.

## 🔮 Future Enhancements

- Integration with Google Maps or another live routing service.
- Real-time traffic information.
- Calendar synchronisation with Google Calendar and Outlook.
- More advanced multi-agent negotiation.
- Full TCP-based agent communication.
- Persistent replay protection and sender-permission validation.
- Machine-learning-based scheduling recommendations.
- Personalised scheduling preferences.

## 🎓 Academic Context

**Project:** BufferWise – Intelligent Day Planner

**Domain:** Artificial Intelligence and Multi-Agent Systems

**Development Environment:** Google Colab

**Interface Framework:** Gradio

## 👩‍💻 Contributors

**[Your Name]**

Computer Science and Engineering – Data Science

[Your GitHub Profile](https://github.com/YOUR-USERNAME)

---

## ⭐ Acknowledgement

This project demonstrates the application of intelligent-agent concepts, rule-based scheduling, BDI decision representation, utility-based coordination and message integrity verification to a practical daily-planning problem.

**BufferWise – Making Every Day More Practical.**
