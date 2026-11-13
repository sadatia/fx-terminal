# SADATIA FX Replay & SMC Practice Terminal v6.7

A professional web-based Forex market replay simulator, Smart Money Concepts (SMC) charting terminal, and risk-managed paper trading workspace. Built for rigorous backtesting, price action study, and trade journaling.

![SADATIA FX Terminal](https://img.shields.io/badge/Version-6.7-2962ff?style=flat-square)
![Docker Ready](https://img.shields.io/badge/Docker-Ready-26a69a?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-787b86?style=flat-square)

---

## 🌟 Key Features

### 1. Dual-Timeframe Synced Charting
* **HTF Bias Reference Pane:** Synchronized higher timeframe chart (M15, H1, H4, D1, W1) with real-time crosshair linking.
* **LTF Execution Pane:** Short-term execution charts with vector drawing overlays and OHLC magnet snap.
* **Auto-SMC Overlay:** Zero-lookahead real-time detection of unmitigated Fair Value Gaps (FVG), Higher Timeframe Order Blocks (OB), Mitigation Blocks (MB), Break of Structure (BoS), and Liquidity Sweeps / Market Structure Shifts (MSS).

### 2. Advanced Drawing Tools & SMC Suite
* **Risk:Reward Tools (`RR+` / `RR-`):** Interactive position planning with automatic R:R calculation, entry/SL/TP drag handles, and one-click export directly to the order ticket.
* **SMC Primitives:** Dedicated drawing tools for FVGs (with auto 50% Consequent Encroachment midline), Order Blocks (with 50% Mean Threshold), Mitigation Blocks, Trend lines, Fib Retracements, Elliot Waves/Paths, and Freehand/Candlestick pens.
* **Workspace Persistence:** Automatically saves all drawings, indicators, and configuration states locally via IndexedDB and `localStorage`.

### 3. Paper Trading & Risk Management Engine
* **Flexible Sizing:** Dynamic Risk % mode (calculating lot size from account balance and Stop Loss distance) or Fixed Lot mode.
* **Advanced Order Management:** Market execution (Buy/Sell @ Bid/Ask with custom spread & commission), Limit/Stop pending orders, multi-target TP1 partial closes (`50%`), and auto-Break-Even (`BE`).
* **Interactive Equity Curve:** Real-time balance and floating equity tracking with hover inspection.

### 4. Trade Journal & Analytics Suite
* **Automated Dual-Stage Snapshots:** Every closed trade automatically captures a high-resolution PNG snapshot of your HTF/LTF chart setup.
* **Performance Breakdown:** Categorizes trades by trading session (Asia, London, NY Overlap, NY), weekday, setup tag, win rate, average R-multiple, profit factor, and maximum drawdown.
* **CSV Export:** Full trade history export compatible with Excel, Notion, and TradingView journals.

---

## 📂 Project Structure

```text
fx-terminal/
├── History-Data/         # Historical OHLCV datasets grouped by symbol
│   ├── EURUSD/
│   ├── GBPJPY/
│   ├── GBPUSD/
│   ├── USDCAD/
│   └── XAUUSD/
├── index.html            # Complete standalone single-file frontend app
├── nginx.conf            # Nginx server config with gzip, CORS, and data routing
├── Dockerfile            # Lightweight Alpine Nginx container build spec
└── docker-compose.yml    # Docker Compose deployment configuration
```

---

## 🚀 Getting Started & Docker Deployment

The application is fully containerized and designed to run with Docker and Docker Compose. Historical market data is dynamically scanned from your host `./History-Data` directory.

### Prerequisites
* [Docker](https://docs.docker.com/get-docker/) & [Docker Compose](https://docs.docker.com/compose/install/) installed on your server or local machine.

### Quick Start

1. Clone your repository:
   ```bash
   git clone https://github.com/sadatia/fx-terminal.git
   cd fx-terminal
   ```

2. Add your historical CSV/JSON tick or bar data inside `History-Data/<SYMBOL>/` (e.g., `History-Data/XAUUSD/m1.csv`).

3. Build and spin up the container:
   ```bash
   docker compose up -d --build
   ```

4. Open your browser and navigate to:
   ```text
   http://localhost:5590
   ```

---

## ⌨️ Keyboard Shortcuts Reference

| Shortcut | Action |
| :--- | :--- |
| <kbd>Space</kbd> | Play / Pause Replay |
| <kbd>&rarr;</kbd> / <kbd>&larr;</kbd> | Step Forward / Step Backward |
| <kbd>1</kbd> &ndash; <kbd>7</kbd> | Timeframes M1 &ndash; W1 |
| <kbd>Alt</kbd> + <kbd>H</kbd> | Toggle HTF Split Pane |
| <kbd>Alt</kbd> + <kbd>K</kbd> | Toggle PDH/PWH Key Levels |
| <kbd>Alt</kbd> + <kbd>S</kbd> | Toggle Killzone Session Shading |
| <kbd>Shift</kbd> + <kbd>B</kbd> / <kbd>S</kbd> | Market Buy @ Ask / Sell @ Bid |
| <kbd>Alt</kbd> + <kbd>E</kbd> / <kbd>P</kbd> / <kbd>X</kbd> | Move SL to Net BE / Partial Close 50% / Close All |
| <kbd>J</kbd> | Open Trade Journal & Analytics Modal |
| <kbd>?</kbd> | Open Shortcuts Help Modal |

---

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.
