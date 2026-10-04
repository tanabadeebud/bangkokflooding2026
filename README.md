# Bangkok Flood 2026 — Event Dashboard

A static, bilingual (TH/EN) flood-event monitoring dashboard for the September 2026 Bangkok flooding, built to match the visual style and page structure of [`hatyaiflooding2025`](https://tanabadeebud.github.io/hatyaiflooding2025/) and [`nanflooding2026`](https://tanabadeebud.github.io/nanflooding2026/), reskinned with the Radar4Flood brand palette for consistency with [radar4flood.com](https://radar4flood.com).

## Pages

1. **index.html** — Summary: a sourced timeline of the Sep 24–27, 2026 event, response measures, and verified impact figures.
2. **weather_data.html** — Weather Data: surface weather map and low-level wind map, each as a time-series slideshow, with a short narrative on the meteorological cause (monsoon trough).
3. **rainfall_stations.html** — Rainfall Station Data: station map, per-station graphs, and a multi-station comparison chart.
4. **radar_animation.html** — Radar Rainfall Animation: hourly/accumulated radar playback on a map.
5. **spatial_radar.html** — Spatial Radar Rainfall: zonal (district/sub-district/sub-basin) radar accumulation analytics.
6. **daily_radar.html** — Daily Radar Rainfall Accumulation: day-by-day accumulated radar maps (same layout as the Hat Yai dashboard's `daily_radar.html`).

## ⚠️ Important: this ships with SAMPLE / PLACEHOLDER data

Per your choice to "build with placeholder data now," everything in `data/` and `data_json/` is synthetic:

- The weather/wind map images (`data/synoptic/*.jpg`, `data/wind/*.jpg`) are generated placeholder graphics, clearly watermarked "SAMPLE / PLACEHOLDER."
- The rain-gauge stations in `data/stations_list.json` are labeled `[SAMPLE]` and are not real station names/locations.
- The radar matrices in `data_json/` and the boundary files in `data/*.geojson` are synthetic (a Gaussian rainfall bump centered near Khlong Chan/Bueng Kum, matching the real event's hardest-hit area, but the numeric values are not measured data).
- The **Summary** page (`index.html`) is the one exception — its timeline and the handful of figures marked as verified (≈300mm/48h, 50/50 districts, 3 deaths, 37 roads cut) are grounded in public news reporting (Al Jazeera, CNN, SBS News, Taipei Times, Wikipedia). Everything else on that page not explicitly sourced is marked "not yet officially published."

**Before using this for real monitoring**, replace:
- `data/*.geojson` with real Bangkok administrative/basin boundaries
- `data/stations_list.json`, `time_control_stations.json`, `station_rainfall_matrix.json` with real telemetry
- `data_json/data_*.json` with real radar matrices (same `{bounds, rows, cols, hourly_matrix, accum_matrix}` shape)
- `data/radar_telemetry_zonal.json`, `time_control_zonal.json` with real zonal telemetry
- `data/synoptic/*.jpg`, `data/wind/*.jpg` with real charts from the Thai Meteorological Department

## Deploying

Same workflow as your other two event dashboards:

1. Create a new GitHub repo named `bangkokflooding2026` (public, so GitHub Pages can serve it for free).
2. Upload all files in this folder, preserving the folder structure (`data/`, `data_json/`, etc.).
3. In the repo's Settings → Pages, set the source to the `main` branch, root folder, and save.
4. Your dashboard will be live at `https://<your-username>.github.io/bangkokflooding2026/`.
5. To link it from the main radar4flood-site as an event page, add a matching `rewrites` block to `vercel.json` (see the updated `vercel.json` delivered alongside this) and a new entry in `js/data.js`'s `events[]` array.
