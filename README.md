# ☁️ NovaAir

> **The Operating System for Atmospheric Health.**
> Digital management of air quality monitoring, industrial emissions auditing, and verified carbon removal credits.

[](https://www.google.com/search?q=https://github.com/novaeco-tech/novaair/actions)
[](https://opensource.org/licenses/MIT)
[](https://www.google.com/search?q=https://air.novaeco.tech)

**NovaAir** is the Vertical Sector responsible for the **Atmosphere**. While `NovaWater` manages the hydrosphere and `NovaNature` the biosphere, **NovaAir** manages the air we breathe. It connects thousands of IoT sensors (particulate, gas, pollen) to create a real-time "Digital Twin" of the sky.

It acts as the compliance engine for the **EU Air Quality Directive** and the **Carbon Removal Certification Framework (CRCF)**.

-----

## 🎯 Value Proposition

Air pollution is the "Invisible Killer," and Carbon Capture is the "Invisible Asset." **NovaAir** makes the invisible visible:

1.  **Public Health Protection:** Providing hyper-local, real-time alerts (e.g., "High PM2.5 at School District 4") to trigger automated ventilation via `NovaInfra`.
2.  **Verified Carbon Removal:** Providing the immutable data proof required to mint high-quality Carbon Credits from Direct Air Capture (DAC) plants or urban forestry.
3.  **Industrial Accountability:** Monitoring smokestack emissions in real-time to enforce "Polluter Pays" taxes via `NovaPolicy`.

-----

## 🏗️ Architecture (The Sky Net)

NovaAir acts as a geospatial time-series database. It relies on the [novaair-worker-air-quality](https://www.google.com/search?q=https://quality.air.novaeco.tech) to ingest the massive firehose of sensor data.

```mermaid
graph TD
    User((City Official)) -->|HTTPS| UI[NovaAir Dashboard]
    UI -->|REST| API[NovaAir API]
    
    subgraph "The Sensing Layer"
        API -->|Fetch Live Data| Worker[Worker-AirQuality]
        Worker -->|Ingest| Infra[NovaInfra (Sensors/Drones)]
        Infra -->|MQTT| DAC[Direct Air Capture Plant]
    end

    subgraph "The Intelligence Layer"
        Worker -->|Stream| Mind[NovaMind]
        Mind -->|Dispersion Model| API
        Mind -->|Toxic Plume Alert| Policy[NovaPolicy]
    end

    subgraph "The Market Layer"
        API -->|Mint Carbon Credit| Trade[NovaTrade]
        API -->|Log Sequestration| Balance[NovaBalance]
    end
```

### Integrated Services

  * **[NovaInfra](https://www.google.com/search?q=https://infrastructure.novaeco.tech):** Manages the hardware network—stationary monitoring stations, mobile sensors on `NovaMobility` buses, and industrial stack sensors.
  * **[NovaMind](https://www.google.com/search?q=https://mind.novaeco.tech):** The meteorologist. Uses Computational Fluid Dynamics (CFD) to predict how a toxic cloud will move through a city based on wind patterns.
  * **[NovaTrade](https://www.google.com/search?q=https://trade.novaeco.tech):** The financial outlet. If a Direct Air Capture plant removes 1 ton of CO₂, NovaAir verifies the sensor logs and tells NovaTrade to mint 1 verified Carbon Token.
  * **[NovaPolicy](https://www.google.com/search?q=https://compliance.novaeco.tech):** The enforcer. If a factory exceeds its NO₂ emissions cap, NovaAir triggers an automatic fine.

-----

## ✨ Key Features

### 1\. The Hyper-Local AQI Map

Standard weather apps use one sensor per city. NovaAir aggregates thousands.

  * **Granularity:** Street-level resolution (10m x 10m).
  * **Data Fusion:** Combines satellite data (Copernicus Sentinel-5P) with ground sensors to fill gaps.

### 2\. Digital MRV for Carbon (Monitoring, Reporting, Verification)

Solves the "Double Counting" problem in carbon markets.

  * **Process:** Connects directly to the flow meters of a Carbon Capture facility.
  * **Verification:** Cryptographically signs the removal data at the source.
  * **Result:** "Grade A" Carbon Credits that trade at a premium on `NovaTrade`.

### 3\. Dynamic Low Emission Zones (LEZ)

Integration with `NovaPolicy` and `NovaLogistics`.

  * **Scenario:** "Air Quality is Critical in City Center."
  * **Action:** NovaAir triggers a dynamic "Congestion Charge" increase via `NovaPolicy`.
  * **Reaction:** `NovaLogistics` automatically re-routes heavy delivery trucks *around* the zone to avoid the fee.

### 4\. Pollen & Allergen Radar

Health-focused analytics.

  * Uses `NovaMind` computer vision on specialized "Pollen Traps" to identify allergen types (Birch, Grass, Ragweed).
  * Sends push notifications to users with registered allergies in `NovaHealth`.

-----

## 🚀 Getting Started

We use **DevContainers** to provide a consistent development environment.

### Prerequisites

  * Docker Desktop
  * VS Code (with Remote Containers extension)

### Installation

1.  **Clone the repo:**
    ```bash
    git clone https://github.com/novaeco-tech/novaair.git
    cd novaair
    ```
2.  **Open in VS Code:**
      * Run `code .`
      * Click **"Reopen in Container"** when prompted.
3.  **Start the Sector:**
    ```bash
    make dev
    ```
      * **Map Dashboard:** http://localhost:3000
      * **API:** http://localhost:8000/docs

### Configuration (`.env`)

```ini
# Air Standards
AQI_STANDARD=EU_CAQI # or US_EPA
CO2_CREDIT_THRESHOLD_TONS=1.0

# Integrations
NOVAINFRA_URL=http://novainfra-api:8000
WORKER_QUALITY_URL=http://novaair-worker-air-quality:8080
NOVATRADE_URL=http://novatrade-api:8000
```

-----

## 📂 Repository Structure

This is a Monorepo containing the sector's specific logic.

```text
novaair/
├── api/                # Python/FastAPI (Domain Logic)
│   ├── src/
│   │   ├── aqi/        # Index calculation logic
│   │   ├── mrv/        # Carbon verification algorithms
│   │   └── dispersion/ # Integration with NovaMind models
├── app/                # React/Mapbox Frontend (The Dashboard)
│   ├── src/
│   │   ├── heatmap/    # WebGL layers for pollution viz
│   │   └── alerts/     # Real-time notification center
├── website/            # Documentation (Docusaurus)
└── tests/              # Integration tests
```

-----

## 🧪 Testing

We use **Atmospheric Simulation** for testing.

  * **Dispersion Test:** `make test-wind`
      * Simulates a gas leak at Point A with North Wind 10km/h. Verifies that sensors at Point B (South) trigger an alert, while Point C (North) stays green.
  * **Credit Minting:** `make test-credit`
      * Feeds raw flow-rate data (1000kg CO₂) into the API. Verifies that exactly 1.0 Credit is minted in the `NovaTrade` mock.

-----

## 🤝 Contributing

We need contributors with backgrounds in **Atmospheric Physics**, **Environmental Data Science**, and **IoT**.
See [CONTRIBUTING.md](https://www.google.com/search?q=../.github/CONTRIBUTING.md) for details.

**Maintainers:** `@novaeco-tech/maintainers-sector-novaair`