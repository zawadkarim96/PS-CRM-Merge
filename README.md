# PS CRM Merge Monorepo

This repository groups two related projects:

- **PS-SALES-main** – Streamlit-based PS Sales Manager application and its Python
  dependencies.
- **PS-Database-main** – Database-related assets and utilities.

## Running the sales app locally

1. Change into the sales project:
   ```bash
   cd PS-SALES-main
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Start Streamlit:
   ```bash
   streamlit run sales_app.py
   ```

## Deploying to Railway

Railway expects a manifest at the service root. Because the app lives in
`PS-SALES-main`, a `railway.toml` is provided at the repo root to point Railway
at the correct directory.

- **Build command:** `cd PS-SALES-main && python3 -m pip install --upgrade pip && python3 -m pip install -r requirements.txt`
- **Start command:** `cd PS-SALES-main && streamlit run sales_app.py --server.port $PORT --server.address 0.0.0.0`
- **Data directory:** Set via `PS_SALES_DATA_DIR=/workspace/data` to use a
  writable path inside the container.

When creating a Railway service, simply use this repository as the root; the
configuration file handles routing Nixpacks to the sales application.
