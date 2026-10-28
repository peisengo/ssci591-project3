# Los Angeles County DMV Office Finder

## What this map shows

This interactive map helps users explore California DMV locations within Los Angeles County. A searchable directory and clickable map show each location's name, address, ZIP code, and facility identifier. The inventory includes specialized DMV facilities, so users should confirm services and appointments on the official DMV website before visiting. It does not show live wait times or current operating status.

## Starting sample

The application adapts Esri's [Intro to FeatureLayer](https://developers.arcgis.com/javascript/latest/sample-code/intro-featurelayer/) sample. It retains the sample's CDN loading, `arcgis-map` component, FeatureLayer service connection, renderer, popup, and map navigation approach. The application uses ArcGIS Maps SDK for JavaScript 5.1.

## What I changed

I replaced the sample's tree dataset with DMV locations and changed the opening extent to the county's locations, including Catalina Island. I changed the hybrid basemap to a light gray basemap, replaced the tree symbols with blue circles, and rewrote the page title and popups. Additional changes include a toggleable county outline, a searchable directory that filters both the list and map, and responsive layouts for smaller screens.

## Data source

The point data comes from the California DMV's [Department of Motor Vehicles Office Locations](https://www.arcgis.com/home/item.html?id=ca1d87b21cb14989bf2946976244c3c9).

Service URL: https://services6.arcgis.com/8zbIxywG5xu2vq8a/arcgis/rest/services/Department_of_Motor_Vehicles_Office_Locations/FeatureServer/0

The county boundary comes from [U.S. Census Bureau TIGERweb](https://tigerweb.geo.census.gov/arcgis/rest/services/TIGERweb/State_County/MapServer/1). Both sources are loaded through FeatureLayer connections. I chose the DMV dataset because it provides authoritative locations and useful address attributes. Because the data has no county field, the application requests county GEOID 06037 and spatially intersects DMV points with that polygon. It then uses the resulting object IDs to restrict the live DMV layer. No downloaded point file drives the map. The verified source returned 34 locations on October 28, 2026; the application calculates the count again on every load.

## Component I added

I retained the sample's Legend to explain the symbols and county outline, and added Home and Scale Bar components. Home returns to the initial overview, and Scale Bar shows distance. A custom search box matches names, addresses, or ZIP codes. Selecting a directory entry zooms to the location and opens its attribute popup.

## Problems and what I'd improve next

Address text alone cannot identify every county location because many offices are in other cities. Polygon intersection solves this problem and includes Catalina Island. Specialized facilities are mixed with regular offices, and no reliable facility-type field is supplied. Future improvements could add verified service categories and office-specific links. The map requires internet access and depends on the public services remaining available.

## Credits

California DMV supplied the location data. The U.S. Census Bureau supplied the boundary. Esri supplied the SDK, basemaps, and starting sample. OpenAI Codex assisted with source verification, implementation, interface design, debugging, and documentation. Review and understand the code before submitting it as coursework.

---

## Run and publish

Open `index.html` through a local web server or publish it on GitHub Pages. There is no build step, framework, API key, or backend. For local preview, run `python -m http.server 8765` in this folder and visit http://localhost:8765.

For GitHub Pages, upload `index.html` and this README to the repository root. In **Settings → Pages**, choose **Deploy from a branch**, the **main** branch, and **/ (root)**. Test the resulting public URL in a private browser window and submit both that URL and the repository URL on Brightspace.
