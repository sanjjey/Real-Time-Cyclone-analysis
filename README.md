# Real-Time Cyclone Detection & Correction

**A Physics-Informed AI System for Live Cyclone Tracking**

### 🚀 Overview
Project AINDRA is a prototype decision support system designed to improve cyclone track forecasting. Unlike traditional models that rely solely on historical data or pure physics, this system combines **Real-Time Atmospheric Data** with **Physics-Informed Neural Networks (PINNs)** to detect "Saddle Points"—critical regions where storms stall or behave erratically.

This system operates in **Real-Time**, fetching live data from the Open-Meteo API to analyze current atmospheric conditions. It features intelligent branching logic to distinguish between active cyclone threats and normal weather patterns.

### ✨ Key Features
* **📡 Real-Time Data Ingestion:** Fetches live atmospheric data (Wind Speed, Geopotential Height) for any location via the Open-Meteo API.
* **🧠 Hybrid AI Model:** Uses a custom `ReSA_ConvLSTM` (Residual Self-Attention) model to correct trajectory bias.
* **⚛️ Physics-Informed Loss:** Enforces thermodynamic limits to ensure AI predictions remain physically realistic.
* **🛑 Stall Detection:** Automatically calculates steering flow to identify dangerous "stalling" phases (Saddle Points) before they happen.
* **⚡ Smart Genesis Check:** Includes branching logic to automatically suspend the heavy AI pipeline when no active system is detected (Wind speed < 30 km/h).
* **📊 Dynamic Visualization:** Plots live trajectory corrections against standard forecast models only when an active threat exists.

### 🛠️ Tech Stack
* **Language:** Python
* **Deep Learning:** PyTorch (ConvLSTM, PINN)
* **Data Source:** Open-Meteo API (Live GFS Data)
* **Physics Engine:** Custom MetPy calculations for Steering Flow & Deep Layer Mean (DLM)
* **Visualization:** Matplotlib & Pandas

### ⚙️ How It Works
1. **Live Scan:** The system queries live satellite data for a target coordinate (default: Bay of Bengal).
2. **Genesis Check:**
   - **Branch A (Calm):** If winds are < 30 km/h, it reports local weather and enters "Monitoring Mode."
   - **Branch B (Storm):** If winds are > 30 km/h, it activates the full AINDRA Pipeline.
3. **Physics Analysis:** It calculates the "Steering Flow" to detect if the storm is moving or stalling.
4. **AI Correction:** The `CycloneTrackCorrector` model predicts a lat/lon shift based on hidden atmospheric patterns.
5. **Decision Support:** A risk algorithm combines probability and impact to generate an alert level (Yellow/Orange/Red).
### 📦 Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/sanjjey/Real-Time-Cyclone-analysis.git](https://github.com/sanjjey/Real-Time-Cyclone-analysis.git)
