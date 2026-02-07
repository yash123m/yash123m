# Bitcoin Quant Trading & Portfolio Allocation System

This repository outlines a **production-grade blueprint** for a Bitcoin trading, portfolio allocation, and monitoring system that integrates advanced indicators, machine learning, and risk management while dynamically allocating profits into low-risk instruments such as **gold, EPF, and FD**.

> ⚠️ **Disclaimer:** This document is for educational and research purposes only. It is not financial advice. Always comply with local regulations, exchange rules, and risk controls.

---

## ✅ Core Objectives

- Extract high-resolution **BTC historical & live market data** from CoinDCX.
- Apply **technical indicators** (e.g., SAR, SuperTrend, volatility bands, regime filters).
- Train **ML/AI models** (LSTM + Transformer/TCN hybrid) for prediction & regime detection.
- Use **fuzzy logic & nearest neighbors** to adapt risk sizing and trade decision logic.
- Execute **smart stop-loss** and **dynamic investment sizing** based on bull/bear sentiment.
- **Allocate 50% of realized profits** into **gold, EPF, and FD**.
- Provide a **refreshing dashboard** with real‑time positions, P/L, and allocation metrics.

---

## 1) System Architecture

```
┌──────────────────────────┐
│   Data Acquisition Layer │  <-- CoinDCX API + Historical CSV
└────────────┬─────────────┘
             │
┌────────────▼─────────────┐
│ Feature Engineering      │  <-- Indicators + Volatility + Sentiment
└────────────┬─────────────┘
             │
┌────────────▼─────────────┐
│ ML & Regime Modeling     │  <-- LSTM + Transformer/TCN + KNN
└────────────┬─────────────┘
             │
┌────────────▼─────────────┐
│ Decision Engine          │  <-- Fuzzy logic + Risk sizing + SL/TP
└────────────┬─────────────┘
             │
┌────────────▼─────────────┐
│ Execution + Portfolio    │  <-- Orders + Profit allocation
└────────────┬─────────────┘
             │
┌────────────▼─────────────┐
│ Dashboard & Monitoring   │  <-- Live P/L + positions + curves
└──────────────────────────┘
```

---

## 2) Data Requirements

### 🔹 Market Data
- **CoinDCX API** (live + historical)
- Timeframes: `1m`, `5m`, `15m`, `1h`, `4h`, `12h`, `1D`

### 🔹 Indicators
- **Parabolic SAR**
- **SuperTrend**
- **ATR / Volatility Index**
- **EMA / SMA / VWAP**
- **RSI / MACD / Stoch RSI**
- **Orderbook imbalance** (if available)
- **Fear & Greed Index** (external source)

---

## 3) ML + AI Modeling

### ✅ Recommended Model Stack
| Layer | Technique | Purpose |
|------|----------|---------|
| Baseline | LSTM | Sequence prediction |
| Advanced | Temporal Transformer / TCN | Long-range pattern detection |
| Auxiliary | KNN + Correlation | Similar market regimes |
| Control | Fuzzy Logic System | Dynamic sizing & decision fusion |

### ✅ Hyperparameter Tuning
- Bayesian optimization or Optuna
- Tuned separately for each timeframe
- Rolling-window backtesting (walk-forward)

---

## 4) Fuzzy Logic Decision Engine

**Inputs:**
- Trend strength
- Volatility regime
- Sentiment (fear/greed)
- Momentum confirmation

**Outputs:**
- Position size (0 → max leverage allowed)
- Stop-loss multiplier
- Profit booking threshold

---

## 5) Trade Management Strategy

### 📌 Profit Booking
- Partial booking at **1R**, **2R**, **3R**
- Apply trailing stop after 1R
- Allocate **50% of realized profit** to:
  - Gold ETF or physical gold
  - EPF contributions
  - FD ladder

### 📌 Smart Stop Loss
- ATR-based dynamic SL
- Volatility regime adjustment
- Market regime override (bull/bear)

---

## 6) Dashboard Requirements

The dashboard should refresh on every iteration and show:

✅ **INVESTED capital**
✅ **Expected return (open positions)**
✅ **Estimated loss (if SL triggered)**
✅ **Number of open positions**
✅ **Number of closed positions**
✅ **Net P/L**
✅ **Equity curve graph** (from start)

Optional additions:
- Trade journal table
- Latest model confidence score
- Regime label (bull/bear/sideways)

---

## 7) Suggested Tech Stack

- **Python** (data + ML)
- **PyTorch / TensorFlow** for deep learning
- **TA-Lib / Pandas TA** for indicators
- **Optuna** for tuning
- **FastAPI** for execution + orchestration
- **Streamlit / Dash** for dashboard
- **PostgreSQL / SQLite** for storage

---

## ✅ Next Steps

1. **Implement CoinDCX data extractor**
2. Build feature engineering pipeline
3. Train baseline LSTM model
4. Add transformer/TCN & tuning
5. Integrate fuzzy sizing logic
6. Build dashboard view
7. Connect profit allocation rules

---

If you'd like, I can scaffold the full codebase (data pipeline, models, backtester, and dashboard) in this repo.
