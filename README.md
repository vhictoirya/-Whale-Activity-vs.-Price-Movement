## Whale Activity vs. Price Movement Analysis

#### This project explore:

- Whale activity trends over time
- Price correlations with whale transaction volume and count
- Lag analysis (do whales move before price changes?)
- Volatility analysis

#### Project Workflow:

1. Environment Setup & Library Installation

- requests — API calls
- pandas / numpy — Data processing
- matplotlib / seaborn — Visualization
- joblib — Saving & loading datasets
- dotenv — Environment variable management
- dune-client — Dune Analytics API access

2. CoinGecko API Integration

- Endpoint: https://pro-api.coingecko.com/api/v3/

##### Data Fetched:

- Historical prices (daily)
- Market caps
- Total volumes

##### Steps:

- Load API key from .env (GECKO_API).
- Fetch 90 days of WBTC price data in USD.
- Convert to pandas DataFrames and save as .pkl in /database.

3. Dune Analytics API Integration
Dune Query Link: https://dune.com/queries/5618550 - (Custom WBTC whale transaction query)

##### Data Fetched:

- Sender & Receiver addresses
- Transaction time
- USD value per transaction

##### Steps:

- Load API key from .env (DUNE_API_KEY).
- Retrieve latest query results.
- Convert to pandas DataFrame.
- Save as .pkl in /database.


4. Data Visualization

- Dual-axis plots: WBTC price vs. whale volume
- Correlation heatmaps
- Lagged scatter plots: whale activity vs. next-day price change
- Volatility vs. whale volume trends

5. Project Structure

├── database/

│   ├── WBTC_prices.pkl

│   ├── WBTC_mcaps.pkl

│   ├── WBTC_total_volumes.pkl

│   ├── WBTC_dune_data.pkl

├── .env

├── requirements.txt

├── analysis_notebook.ipynb

└── README.md

6. Environment Variables

- Create a .env file in the project root with:
    - GECKO_API=your_coingecko_api_key
    - DUNE_API_KEY=your_dune_api_key

7. Key Insights

- There are no strong linear correlation between whale activity and daily price change.
- Lag analysis shows no immediate cause-effect between whale activity and next-day price change or volatility.
- Large whale days occur at both price highs and lows, this suggests whale transactions are not a standalone short-term price predictor.