# Wix Embed Setup: Seasonal Tank Temperature Chart

## 1. Host the HTML and CSV

You need both files publicly reachable over HTTPS:

- `wix_tank_temperature_chart.html`
- Your CSV file (for example `FullDS_Findhorn_30min.csv`)

Any static hosting works (Wix media/public file URL, GitHub Pages, Netlify, S3 static website, etc.).

## 2. Add the chart in Wix

1. In Wix Editor, add an **Embed** element.
2. Choose **Embed a Widget**.
3. Set the URL to your hosted HTML file and pass the CSV URL as a query parameter:

```text
https://YOUR_HOST/wix_tank_temperature_chart.html?csv=https%3A%2F%2FYOUR_HOST%2FFullDS_Findhorn_30min.csv
```

4. Resize the embed area to at least 700x500 for desktop.

## 3. If you do not want query parameters

Edit this line in `wix_tank_temperature_chart.html` and republish:

```js
const DEFAULT_CSV_URL = "https://example.com/FullDS_Findhorn_30min.csv";
```

Replace the placeholder with your real public CSV URL.

## 4. Expected CSV columns

The chart expects these exact headers:

- `Time`
- `Tank Bottom [°C]`
- `Tank Mid [°C]`
- `Tank Mid Hi [°C]`
- `Tank Top [°C]`

## 5. Troubleshooting

- If chart says fetch failed, confirm the CSV URL opens directly in a browser.
- If chart says CORS issue, enable cross-origin access on the host serving CSV.
- If a season button is disabled, that season has insufficient usable data.