# Trufi MBTiles Generator

Part of the [Trufi Association](https://trufi-association.org/) toolkit for building transit apps.

Generate MBTiles files from OpenStreetMap data (.osm.pbf).

## Requirements

- Docker

## Quick Start

1. Place your `.osm.pbf` file in the `data/` folder
2. Copy `.env.example` to `.env` and configure:
   ```bash
   cp .env.example .env
   ```
3. Edit `.env` with your city name and preferences
4. Run:
   ```bash
   docker compose up
   ```

The `.mbtiles` file will be generated in `data/`.

## Configuration

| Variable | Description |
|----------|-------------|
| `CITY_NAME` | City name (used for input/output filenames) |
| `MAX_ZOOM` | Maximum zoom level (recommended: 14) |
| `MIN_ZOOM` | Minimum zoom level (recommended: 0) |
| `JAVA_MEMORY` | Java heap memory (e.g., `4g`, `8g`) |
| `THREADS` | Number of processing threads |

### Finding your available threads

**macOS:**
```bash
sysctl -n hw.ncpu
```

**Linux:**
```bash
nproc
```

**Windows (PowerShell):**
```powershell
(Get-CimInstance Win32_Processor).NumberOfLogicalProcessors
```

### Example

To generate tiles for Bogota with higher zoom:

```env
CITY_NAME=bogota
MAX_ZOOM=16
MIN_ZOOM=0
JAVA_MEMORY=8g
THREADS=8
```

Then place `bogota.osm.pbf` in `data/` and run `docker compose up`.

## Get OSM Data

- **Cities:** [trufi-pbf-extractor](https://github.com/trufi-association/trufi-pbf-extractor) (recommended)
- **Countries/Regions:** [download.geofabrik.de](https://download.geofabrik.de/)

## License

GPL-2.0
