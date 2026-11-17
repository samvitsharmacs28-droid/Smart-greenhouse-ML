# Results summary — Smart Greenhouse Automation System
*Compartment AICU, AGC 2nd edition · test period 02 May – 26 May 2020 · 6,828 five-minute steps*

| Target | Best model | Accuracy | Within tolerance | R² | RMSE | MAE | Skill vs persistence |
|---|---|---|---|---|---|---|---|
| Tair_t+30 | RandomForest | 98.25% | 91.1% (±1) | 0.975 | 0.59 °C | 0.41 | +20.5% |
| Tair_t+60 | RandomForest | 97.41% | 83.5% (±1) | 0.954 | 0.79 °C | 0.60 | +35.0% |
| Rhair_t+30 | LightGBM | 95.99% | 83.9% (±5) | 0.869 | 4.15 % RH | 2.70 | +0.3% |
| Rhair_t+60 | LightGBM-tuned | 93.82% | 70.7% (±5) | 0.730 | 5.94 % RH | 4.17 | +2.3% |

- **Uncertainty:** after conformal calibration, the 80 % intervals contained the true value 67–79 % of the time (raw quantile bands: 55–64 %).
- **Decision accuracy:** ventilation commands were correct 93.7% of the time with forecasts.
- **ROC-AUC (ventilate):** 0.985 with forecasts vs 0.973 with current readings.
- **Control:** ventilation decisions reached F1 0.929 with forecasts vs 0.908 with a reactive thermostat.
- **Early warning:** median 15 min before the 25 °C threshold was crossed (25 events).
- **Explainability:** the strongest drivers of the 60-min temperature forecast were hour_sin, PipeLow, hour_cos.
- **Horizon (Lab A):** ML skill over persistence peaks at 42% for the 120-min forecast.
- **Sensors (Lab B):** indoor sensors alone give 22.0% skill; the best set (actuator states) gives 28.8%, and all sensors 22.2%.
- **Robustness (Lab C):** DHT22-level sensor noise changes 60-min RMSE by +11%; with the outdoor station offline it changes by +11%.
- **What-if controller (Lab E):** at 05-14 09:25 it recommended vents 0 % and pipe 0 °C (predicted 24.5 °C; actual with the real settings 25.2 °C).
- **Data needed (Lab D):** 3 days of history already beat the persistence baseline.

**Limitations:** one season (Dec 2019 – May 2020), one crop (cherry tomato), a high-tech Dutch glasshouse; published scores from other datasets are not directly comparable.