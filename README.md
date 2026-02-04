# ⚽ Predicting_PL_Games

**Predicting Premier League games for the 2025-2026 season**

# 🏟️ Premier League Predictions 2025-2026 - Value Betting AI

This project uses machine learning, live **Sports Odds API** data, and historical Premier League results to predict match outcomes and identify value bets for the 2025-2026 Premier League season.

## 🚀 Project Overview

This repository contains a **Random Forest Machine Learning model** that predicts match results (Home Win, Draw, Away Win) and other markets like BTTS and Double Chance. It compares these predictions against live bookmaker odds to find "Value Bets"—instances where the bookmakers have underestimated a team's chances.

The model leverages:

* **Historical Data (2023-2026):** Training data from past seasons.
* **Live Odds API:** Real-time betting market data.
* **Advanced Features:** Recent form, Head-to-Head (H2H) history, team strength, and goal averages.

*Over the course of the season, the model updates automatically as new match results are added to the dataset.*

## 📊 Data Sources

* **Football-Data.co.uk:** Fetches historical CSV data for match results, goals, and stats for training.
* **The Odds API:** Fetches live, real-time bookmaker odds for upcoming fixtures (H2H, BTTS, Double Chance, Draw No Bet).

## ⚽ How It Works

1. **Data Collection:** The script downloads the latest season data (2025/26) and historical data (2023-24, 2024-25) automatically.
2. **Preprocessing:** It cleans team names (standardizing "Spurs" to "Tottenham Hotspur") and calculates stats like form (last 5 games) and H2H dominance.
3. **Model Training:** Two **Random Forest Classifiers** are trained:
* **Model A:** Predicts Match Outcome (Home, Draw, Away).
* **Model B:** Predicts Both Teams To Score (Yes/No).


4. **Live Prediction:** You input a match (e.g., "Man Utd vs Spurs"). The tool fetches live odds, runs the prediction, and calculates **Expected Value (EV)**.
5. **Value Analysis:** It highlights bets where `EV > 0%`, spotting mathematical edges against the bookies.

## 📦 Dependencies

* `requests`
* `numpy`
* `pandas`
* `scikit-learn`
* `plotly` (optional for visualization)

Install them via:

```bash
pip install pandas numpy scikit-learn requests plotly

```

## 🔧 Usage

1. **Get an API Key:** Get a free key from [The Odds API](https://the-odds-api.com/).
2. **Paste Key:** Add your key to the `main()` function in the script.
3. **Run the Script Predicting_PL_Games:**

```bash
python Predicting_PL_Games.py

```

4. **Interactive Mode:**
The tool will ask you for the teams. You can use abbreviations!
```text
Enter Match Details:
  Home Team: Man Utd
  Away Team: Spurs

```


5. **Expected Output:**

```text
PREDICTION: Manchester United vs Tottenham Hotspur
=====================================================================================
Home Win        | Model: 36.3% | Fair: 2.75  | Odds: 1.7   | EV: -38.2%
Draw            | Model: 30.0% | Fair: 3.33  | Odds: 4.6   | EV: +38.0% <<< VALUE
Away Win        | Model: 33.7% | Fair: 2.97  | Odds: 5.0   | EV: +68.3% <<< VALUE
-------------------------------------------------------------------------------------
BTTS Yes        | Model: 68.8% | Fair: 1.45  | Odds: 1.62  | EV: +11.4% <<< VALUE
-------------------------------------------------------------------------------------
Home DNB        | Model: 51.9% | Fair: 1.93  | Odds: 1.28  | EV: -33.6%
Away DNB        | Model: 48.1% | Fair: 2.08  | Odds: 3.45  | EV: +65.9% <<< VALUE
-------------------------------------------------------------------------------------
1X (Home/Draw)  | Model: 66.3% | Fair: 1.51  | Odds: 1.22  | EV: -19.1%
X2 (Away/Draw)  | Model: 63.7% | Fair: 1.57  | Odds: 2.2   | EV: +40.1% <<< VALUE

--- MODEL REASONING ---
1. FORM: Manchester United has better form (11 vs 3 pts).
2. BOGEY TEAM: History favors Tottenham Hotspur (H2H Score: -2).
   -> The model detects that the Away team often gets results in this matchup.
3. STRENGTH RATING: Home (64.0) vs Away (32.0)

```

## 📈 Model Performance

The model is evaluated using **Expected Value (EV)**. A positive EV indicates that the model believes the probability of an outcome is higher than what the bookmaker's odds imply.

* **High EV (+5% or more):** Considered a strong value bet.
* **Low/Negative EV:** The market is priced correctly or unfavorable.

## 📌 Future Improvements

* [ ] Incorporate **Expected Goals (xG)** data for deeper performance analysis.
* [ ] Add **Player Availability** (injury news) as a feature.
* [ ] Ensemble Modeling (Stacking): Instead of relying on just one Random Forest model, train multiple models (e.g., XGBoost, Logistic Regression, and Neural Networks) and "stack" them. A "Meta-Learner" then decides which model to trust based on the specific match conditions.

## 📜 License

This project is licensed under the MIT License.

**⚽ Start beating the bookies with Data Science! 🚀**
