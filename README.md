# Open Catastro 360

An open-source, high-performance geospatial data pipeline and management platform designed for continuous municipal property tax assessment and urban planning. This system automates the processing of geo-referenced 360° street-level imagery, indexing visual evidence directly to municipal property registries (e.g., PostGIS) to streamline tax collection and minimize field inspection costs.

## System Architecture Overview

The platform is structured into four decoupled, interoperable layers to ensure low deployment overhead and strict data sovereignty:

* **Field Capture Layer:** Integrates commercial 360° cameras (equirectangular projection) with precision GNSS receivers and mobile data tablets to record frames every 10–15 meters based on predefined priority routes.
* **Ingestion & Processing Layer:** A Python-based backend powered by FastAPI that compresses high-resolution assets, extracts metadata (EXIF/GPS), and implements computer vision filters (YOLOv8) to automatically blur license plates and faces.
* **Geospatial Storage Layer:** A robust PostgreSQL database extended with PostGIS. Spatial queries (`ST_Contains`, `ST_Buffer`) match imagery coordinates directly to cadastral lot polygons.
* **Management & Visualization Client:** A zero-dependency web interface utilizing Leaflet.js for interactive cadastral mapping and Pannellum.js for immersive 360° hardware-accelerated panoramic rendering.

---

## Technical Specifications

### Core Requirements & Software Stack
* **Database:** PostgreSQL 15+ / PostGIS 3.3+ (Spatial indexing using GIST)
* **Backend Engines:** Python 3.11+, FastAPI, Shapely, PyProj
* **Frontend Visualization:** Vanilla JavaScript (ES6), Leaflet.js, Pannellum.js
* **Open Geospatial Consortium (OGC) Compliance:** WMS (Web Map Service), WFS (Web Feature Service)

### Minimum Hardware Baseline (Field Operation)
* **Optical Sensor:** 360° Camera supporting 5.7K equirectangular video or continuous photo capture.
* **Location Receiver:** Multi-band GNSS/GPS with a refresh rate of at least 1Hz.
* **Storage Capacity:** Local storage capable of sustaining write speeds of 100MB/s for continuous data accumulation during 6-hour field shifts.

---

## Roadmap and Iterative Milestones

1. **Phase 1 (Current):** System specification, public documentation, and static municipal information gateway deployment.
2. **Phase 2:** Database schema design, PostGIS extension routing, and GPX/GeoJSON track parsing engine implementation.
3. **Phase 3:** Automated ingestion API with privacy filters (Computer Vision blurring algorithms).
4. **Phase 4:** Production web interface featuring split-screen GIS mapping and 360° panoramic projection.
