
# Predicción del precio de Bitcoin mediante Deep Learning y Análisis de Sentimiento

Este repositorio contiene el código, modelos y documentación asociados al Trabajo de Fin de Máster (TFM) titulado:

> **"Predicción de tendencias en el mercado de Bitcoin mediante redes neuronales profundas y análisis de sentimiento"**  
> Máster en Inteligencia Artificial – Universidad [Nombre]  
> Curso académico 2024–2025

## 📌 Descripción del proyecto

El objetivo principal de este trabajo es explorar si la incorporación de variables de **análisis de sentimiento** —extraídas mediante modelos NLP como **FinBERT**— puede mejorar la capacidad predictiva de modelos de series temporales tradicionales basados en redes neuronales, como **LSTM**, frente a enfoques puramente cuantitativos.

Para ello, se propone una arquitectura híbrida **multimodal** que combina:
- Series temporales financieras (precios, volumen, etc.)
- Indicadores sentimentales (positivos, negativos y neutros)
- Mecanismos de atención y fusión adaptativa
- Optimización bayesiana de hiperparámetros con **Optuna**

El modelo es evaluado frente a benchmarks clásicos como **ARIMA**, **GARCH**, **XGBoost** y **Regresión Lineal**, utilizando métricas como **RMSE** y **MAE**.


## 📊 Datasets utilizados

- Precio histórico diario de Bitcoin (`2010–2025`) desde [Kaggle](https://www.kaggle.com/datasets/svetlinnakov/bitcoin-prices-2010-2024)
- Tweets y titulares financieros procesados con **FinBERT**
- Post de Reddit y Cointelegraph (datasets integrados y alineados por fecha)
- Dataset final fusionado con variables `Close+1`, `Close+3`, `Close+7`, `Close+15`

## 🧠 Modelos implementados

- `Modelo 1:` LSTM apilado con fusión adaptativa
- `Modelo 2:` LSTM + Attention + Fusión adaptativa
- `Baselines:` ARIMA, GARCH, XGBoost, Regresión Lineal, LSTM simple

## 🔍 Resultados destacados

| Modelo                       | RMSE (EUR) | MAE (EUR) |
|-----------------------------|------------|-----------|
| AT-LSTM + Gating            | **2821.97**| **1954.64** |
| LSTM apilado + Gating       | 3032.76    | 2103.38   |
| LSTM simple                 | 4208.24    | 3158.38   |
| XGBoost                     | 4011.59    | 2983.90   |
| Regresión Lineal            | 4096.47    | 2744.13   |
| ARIMA                       | 4230.61    | 3462.13   |
| GARCH + AR(1)               | 5438.26    | 4699.38   |
| GARCH + AR(1) (15 días)     | ✖️         | ✖️        |

## 🛠️ Requisitos

```bash
pip install -r requirements.txt
```

Requiere Python ≥ 3.8 y bibliotecas como:
- `TensorFlow`
- `Optuna`
- `xgboost`
- `scikit-learn`
- `pandas`, `numpy`, `matplotlib`, `seaborn`

## 👨‍💻 Autor

- **Nombre completo**: Castañ Aguilella, Salvador | Conesa Cerezuela, Ginés
- **Universidad**: UNIR
- **Director académico**: Ariza Lasarte, Alberto

## 📄 Licencia

Este repositorio se distribuye bajo licencia MIT. Consulta el archivo `LICENSE` para más información.
