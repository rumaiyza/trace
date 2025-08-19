# trace
Visualisation System for Vegetation Trends using Remote Sensing and Satellite Data

## Features
- Location-based vegetation health analysis using opensource data from MODIS and Sentinel-2
- Interactive visual timeline of changes observed in vegetation with per-frame logging
- Comparative vegetation index charting across user input time frames
- Hook-based architecture for extensibility ( Anomaly detection based on NDVI volatility, Optional forecasting via pre-trained models, GeoJSON export of flagged anomalies )

## Setup:
1. Install dependencies: pip install Flask folium geopy pyngrok earthengine-api matplotlib requests numpy Pillow joblib geojson
2. Authenticate Earth Engine using your service account key: ee.Authenticate()
                                                             ee.Initialize(project='your-project-id')
3. Run the notebook. The Flask app will launch and expose a public URL via ngrok.

## Hooks:
- frame_logger: Logs mean pixel value of each saved frame to frame_stats.json
- anomaly_detect: Flags timestamps where NDVI change exceeds ( mean + 2×standard deviation )
- geojson_export: Exports anomaly timestamps as GeoJSON points
- ml_model: Supports vegetation index value prediction using a pre-trained model (not included in repo)

## Potential Enhancements
- Interactive time series chart
- Passive user exploration ( without input specification )
