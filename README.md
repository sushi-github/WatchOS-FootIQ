# ⚽ True Football Data Collector – FootIQ

**FootIQ** is an advanced football activity tracker for iOS and watchOS, built to turn casual matches and training sessions into meaningful data-driven insights. By combining Apple Watch GPS and HealthKit data with AI-powered tactical analysis, it gives players real feedback on how they play — and how to improve.

This project is a solo build over summer (June–September), designed to explore and demonstrate:
- Full-stack development on iOS and watchOS using **Swift**, **SwiftUI**, **CoreLocation**, and **HealthKit**
- The practical integration of **LLMs and machine learning** for personalised sports analytics
- Clean UX, gamified progression, and real-world mobile architecture

This `README.md` includes:
- 🛠️ Feature roadmap
- 🔍 Technical decisions
- 🚧 Development phases
- 📚 Documentation

By bridging mobile development, AI, and real-world performance tracking, FootIQ brings elite-level football analytics to everyday players — with the depth and polish of a production-ready tool.

---
## 🔍 Research and Requirements

**FootIQ** is an innovative application designed for both watchOS and iOS, aiming to bring **comprehensive football activity tracking** to Apple devices.

### ⚠️ Limitations of Native Tracking

Traditionally, the Apple Watch has categorized football as a generic cardio activity, capturing only basic metrics such as:

- 🫀 Heart Rate  
- ⏱️ Duration  
- 🔥 Calories Burned  

This approach **overlooks critical performance indicators** essential for football players — such as **positional data**, **sprint intensity**, and **tactical movements**.

---

### 🆕 Advancements in watchOS

With the release of **watchOS 11**, Apple introduced major updates to its Workout capabilities, including:

- 🛰️ **Distance and Speed Tracking**  
  Utilizes GPS more efficiently to measure player movement.

- 📊 **Effort Rating (RPE)**  
  A new post-match stat that combines heart rate, pace, and personal thresholds to calculate how demanding the session was (1–10 scale).  
  _This mirrors metrics used in sports science like Relative Perceived Exertion._

> Source: [Mingle.Sport — Using Apple Watch to Track Football](https://mingle.sport/blog/use-an-apple-watch-to-track-your-football-workout/?utm_source=chatgpt.com)

---

### ⚽ Why Football Needs Specialised Metrics

Despite these improvements, the **unique demands of football** still aren't fully captured by general-purpose fitness tracking. Key metrics like:

- 🔥 **GPS Heatmaps** – To assess positional tactics and zones covered  
- ⚡ **Sprint Bursts & Running Load** – To measure explosiveness and endurance  
- 🧠 **Match Intelligence** – Goals, assists, cards, etc., essential to player evaluation

While professional leagues use high-end systems (e.g. GPS vests, optical tracking), **amateur players lack access** to these insights — even though they deserve it just as much.

---

### 🧠 The FootIQ Solution

**FootIQ** brings elite-level analytics to grassroots players by combining:

- 📍 **Location-based movement heatmaps**
- ❤️ **Health + sprint + effort data**
- 🧠 **AI-powered tactical insights**
- 🔄 **Role-based overlays (e.g. touchline winger, inverted forward, wingback)**

It empowers players to:

- Understand how they move on the pitch  
- Compare themselves to elite tactical patterns  
- Get feedback on how to improve — or where their true role may lie

---

### ⚠️ Wearable Device Rules in Football

According to the official [IFAB Laws of the Game](https://www.theifab.com/laws/latest/the-players-equipment/?utm_source=chatgpt.com):

> "A player must not use equipment or wear anything that is dangerous."

This includes **watches and smart wearables during official matches**. Therefore:

> 🛡️ **FootIQ is designed for friendlies, kickabouts, and training sessions only** — where these rules are not enforced.

---

## 🎯 Goals

## 📍 Goals & Roadmap

Here's the Development Roadmap as well as Key Goals for the Program to fulfill the Requirements:

- [ ] Seamless GPS & Heart Rate tracking via Apple Watch (CoreLocation + HealthKit)
- [ ] Lightweight watchOS UI for:
  - [ ] Start / Stop controls
  - [ ] Position selection before match
  - [ ] Side switching  
  - [ ] Basic Manual Stat Input UI
  - [ ] Displaying Core Data (HR, Distance, Speed, Calories, Game Time)
- [ ] iPhone-based UI:
  - [ ] Start Up Page asking for Player for Key Info:
    - [ ] Age
    - [ ] Gender
    - [ ] Improve in current Position/Shift to New One? 
  - [ ] Player Profile:
    - [ ] Long-term stat and health tracking
    - [ ] Gamified progression (Increase Valuation based on Performance)
  - [ ] Game Data and Tracks:
    - [ ] Health Data (HR, Steps, Distance, Average and Peak Pace, Calories etc. in relation to Game Time or Position)
    - [ ] GPS-based Heatmaps
    - [ ] Tactical overlays (e.g., touchline winger, inverted fullback)
    - [ ] Manual stat input UI:
      - [ ] Goals
      - [ ] Assists
      - [ ] Match score and opposition level
  - [ ] AI-generated positional feedback (via OpenAI LLM):
    - [ ] Role-based advice ("You’re playing like a fullback…")  
    - [ ] Improvement suggestions for target role

> This section will be updated throughout development (June–September) to track progress.

---

## 🛠️ Tech Stack

FootIQ is engineered to blend low-level device data with high-level tactical insight. The stack reflects a balance between native Apple frameworks, AI capabilities, and scalable architecture choices.

| Layer               | Tools / Frameworks                                           | Purpose                                                                 |
|---------------------|--------------------------------------------------------------|-------------------------------------------------------------------------|
| **Watch App**       | `Swift` · `WatchKit` · `HealthKit` · `CoreLocation`          | Collect live metrics (GPS, HR, movement) in a lightweight session UI   |
| **iPhone App**      | `SwiftUI` · `Combine`                                        | Visualise data, render heatmaps, drive onboarding and profile features |
| **Heatmap Engine**  | `MapKit` (initial)                                           | Overlay positional zones and render GPS movement across 2D pitch maps  |
| **AI Feedback**     | `OpenAI API` · Custom LLM prompt templates                   | Generate tactical advice based on player behaviour and desired role    |
| **Storage Layer**   | `CoreData` (local)                                           | Store game history, session stats, progression & gamified attributes   |
 **UX & Design**     | `Canva` · `Procreate` · `SF Symbols` · `Haptics` · `Animation`| Custom icons, tactical visuals, clean UI graphics & polished UX        |
| **Planning & Docs** | GitHub Projects · GitHub Issues                              | Track development phases, goals and technical documentation            |

---

## 📊 Feature Breakdown

### ⌚ Apple Watch Features

Goal: Provide a lightweight, intuitive tracker that captures essential football performance data and syncs seamlessly with the iPhone app.

| **Feature**                | **Description**                                              | **Tech Stack**                          | **Purpose & Value**                                                                                   |
|----------------------------|--------------------------------------------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------|
| **GPS-based Heatmaps**      | Track player movement in real-time during matches via GPS to convert into GPS Heatmaps | `CoreLocation`, `HealthKit`, `MapKit`, `watchOS` | Core positional data to visualise pitch zones covered and movement patterns                           |
| **Sprint / Heart Rate / Motion Data** | Collect key physical performance metrics like heart rate, sprint bursts, and pace | `HealthKit`, `WorkoutKit`, Apple Watch sensors | Adds a physical dimension to tactical insights, enabling layered analysis of fitness and intensity  |
| **Side Switch Handling**    | Mark pitch side changes during halves                        | watchOS toggle UI                     | Ensures heatmaps correctly represent player positioning when switching pitch orientation             |
| **UI**                     | Minimal watchOS UI controls to start/stop tracking, select position before match, and add basic match events in real time. Display health and fitness metrics to the user | `SwiftUI`, `WatchKit`, `WorkoutKit`  | Keeps in-game interactions simple while linking data to player role and context                      |

---

### 📱 iOS App Features

Goal: Act as the central hub for data visualization, player profiling, and AI-driven tactical coaching.

| **Feature**                | **Description**                                              | **Tech Stack**                        | **Purpose & Value**                                                                                   |
|----------------------------|--------------------------------------------------------------|-------------------------------------|-----------------------------------------------------------------------------------------------------|
| **Player Positional Profile Setup** | Onboarding form capturing preferred position, target role, and shooting foot | `SwiftUI`, `CoreData` or `UserDefaults` | Personalises feedback, heatmaps, and tactical overlays based on player context                        |
| **Tactical Overlay Comparison** | Overlay heatmaps with elite-level positional templates | Custom pitch rendering with `MapKit`/Canvas, JSON zone data | Helps players compare their positioning to ideal tactical roles (e.g., inverted winger vs touchline winger) |
| **LLM Personal Coach**    | AI-generated tactical feedback based on tracked data and player role | `OpenAI API`, LLM prompts, `SwiftUI` display | Offers insightful, role-specific advice to refine positioning and decision-making                     |
| **Manual Match Input**      | Input match stats such as score, goals, assists, and opponent level | `SwiftUI`, `CoreData` or serverless backend | Provides contextual data to enrich analysis and player rating accuracy                               |
| **AI Match Rating Engine**  | Automated player ratings mimicking popular football analytics | Custom formulas, regression models, GPT fine-tuned prompts | Delivers quantitative performance scores with detailed commentary                                   |
| **Gamified Progression**    | Track player progression in tactical discipline, speed, and involvement | `CoreData`, badges/unlock system | Boosts engagement by rewarding skill growth and tactical mastery in a relevant way (Player Values)    |

---

## 🚀 Future Additions

Goal: Extend FootIQ beyond individual tracking to offer team-wide performance analysis and coaching insights.

| **Feature**            | **Description**                                                                                      | **Tech Stack**                    | **Purpose & Value**                                                                                   |
|------------------------|----------------------------------------------------------------------------------------------------|---------------------------------|-----------------------------------------------------------------------------------------------------|
| **Team Tracking**      | Track overall team performance and compare individual stats with teammates for deeper insight      | `Firebase`, `iCloud`, `CoreData` | Enables players to see how they rank within their team, fostering competition and collaboration      |
| **Coach Mode**         | Provide coaches with aggregated team insights, formation advice, and tactical recommendations       | `Shared Apple ID`, `AirDrop`, AI/ML models | Helps coaches optimise lineups, tactics, and player combinations based on data-driven analysis       |
| **Team Tactical Overlays** | Visualise team formations and collective positional trends to identify strengths and weaknesses   | Extended `MapKit`, custom visualizations | Supports coaches in evaluating team shape and tactical adherence                                   |
| **Match & Training Reports** | Auto-generate detailed reports on team and player performance with actionable insights           | PDF generation, Data viz libraries | Delivers comprehensive feedback for players and coaches to improve performance                      |
| **Player Development Tracking** | Monitor player progress over time with coach annotations and personalised growth plans          | `CoreData`, Cloud sync, annotation tools | Enables long-term development planning tailored to each player’s needs                              |
| **Potential Shot Tracking** | Detect when a shot has been taken to be marked as on target in game or post game for shot analysis | Sensors to detect sudden drop in Pace/Connections to Foot Pods to capture change in momentum| Adds another layer of analysis for crucial to Forwards and overall output analysis and shot economy|

---

## 💡 Example Use Case

> User A downloads the app  
> - Age: 20  
> - Gender: Male  
> - Wants to Change Position  
> - Current Position: Right Wing-Back (RWB)  
> - Preferred Position: Right Winger (RW)

### Step 1: Onboarding & Profile Setup  
User A opens FootIQ on iPhone and fills out the onboarding form, specifying his current and preferred playing positions along with basic info. This data helps personalise the tactical feedback and heatmap overlays he will receive.

### Step 2: Pre-Match Setup on Apple Watch  
Before starting a match or training session, User A uses the minimal watchOS interface to select he position he is playing in this match (RW), enabling accurate contextual tracking. He can also mark pitch side switches to ensure the heatmap correctly reflects his movements relative to the pitch during half times for example.

### Step 3: Match Tracking  
During the game, the Apple Watch tracks User A’s GPS location, heart rate, sprints, and motion data in real-time. 
The watch app records all movement and physical metrics with minimal interaction required from the player. 
User A can also add in Goals Contributions he provided, as well as Cards received.
On the watch, basic health tracking is displayed such as HR, Steps, Distance Covered, Average and Peak Pace, and Time

### Step 4: Post-Match Analysis on iPhone  
After the match, User A syncs his data to the iPhone app where:

- His GPS heatmap visualises areas covered on the pitch as a RW, compared to standard RW positional templates.
- Physical performance metrics (e.g., sprint bursts, average pace, heart rate zones) are presented alongside movement data.
- AI-driven feedback from the LLM personal coach analyses his positioning, suggesting improvements to align better with the RW role.
- Manual input allows User A to add goals, assists, cards here too as well as match context like opponent difficulty and scoreline for richer insights.

### Step 5: Tactical Insights & Progression  
Based on collected data and AI advice, User A can:

- Understand if his movements align better with his current RWB role or his preferred RW role.
- Receive personalised drills and tactical tips to transition smoothly to RW.
- Track progression over multiple matches via gamified metrics that boost engagement and reflect skill growth.

---

### Broader Impact  
FootIQ bridges the gap between casual football players and professional-level data analytics by offering a user-friendly, data-driven approach to understanding and improving football performance — all through the power of Apple Watch sensors, iOS visualisation, and AI coaching.

---

## 🔐 License

MIT – Free to use and contribute to. If you build on it, let me know!

---

## 🚀 Author

**Sushant Nepal**  
Passionate about football, tactical data, and building practical AI systems.  
🔗 [github.com/sushi-github](https://github.com/sushi-github)
✉️ [Contact Me](psysn2@nottingham.ac.uk)

---

## 📆 Timeline

- 🗓️ May: Research & Planning ✅  
- 🗓️ June–July: Core Feature Build 🔧  
- 🗓️ August: AI Integration & Polishing 🧠  
- 🗓️ September: Polish, Testing, and Demo 🚀
