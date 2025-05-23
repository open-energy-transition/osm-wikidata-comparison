# OSM-WIKIDATA Toolset
This repository contains a set of tools to extract, transform and analyze wikidata electricity infrastructure information and asses its potential integration to Open Street Map.

Currently, the repository has two python scripts:

  1. compare_osm_wikidata_powerplants.py, which is an OSM vs wikidata powerplant matching script.
  2. get_wiki_substations.py, which fetches classes and subclasses of substations in wikidata to generate a new dataset grouped by country.


## OSM vs Wikidata Power Plant Comparison

This Python script compares power plant data between **OpenStreetMap (OSM)** and **Wikidata**. It fetches data from both sources using APIs, performs comparisons based on geographic proximity and name, and identifies missing power plants or coordinate mismatches. The comparison results are saved in **CSV** and **GeoJSON** formats.

## Features
- Fetches power plant data from Wikidata using the SPARQL API.
- Fetches power plant data from OpenStreetMap using the Overpass API.
- Compares the datasets based on geographic proximity and name matching.
- Identifies missing power plants and coordinate mismatches between OSM and Wikidata.
- Outputs the comparison results in CSV files, geoJSON file for missing data in OSM and quickstatement file for missing data in wikidata

## CSV Files Output
The script generates the following CSV files containing valuable matched/unmatched data:
- **`wikidataset.csv`**: Contains the power plants fetched from Wikidata.
- **`osm_api_dataset.csv`**: Contains the power plants fetched from OpenStreetMap.
- **Comparison Results CSV Files**:
  - **`missing_in_wikidata.csv`**: Lists power plants missing in Wikidata but found in OSM.
  - **`coordinate_mismatches_missing_wikidata.csv`**: Lists coordinate mismatches in Wikidata.
  - **`wikidata_missing_coordinate.csv`**: Lists Wikidata entries missing coordinates.
  - **`missing_in_osm.csv`**: Lists power plants missing in OpenStreetMap but found in wikidata.
  - **`coordinate_mismatches_missing_osm.csv`**: Lists coordinate mismatches in the missing data from OpenStreetMap.
  - **`missing_in_osm.geojson`**: GeoJSON file composed of missing powerplants in OSM. 
  - **`missing_in_wikidata.qs`**: Quickstatement file with missing powerplant data in wikidata

## Wikidata Power Substation Extraction

This Python script extracts and organizes power substation data from Wikidata. It fetches substation data by country using the SPARQL API, classifies substations by verified types (e.g., electrical substations, HVDC converter stations), and outputs the results in CSV and GeoJSON formats.

## Features

- Fetches substation data from Wikidata using the SPARQL API.
- Counts and groups substations by country and type.
- Retrieves detailed substation information including geographic coordinates, type, and label.
- Splits the dataset into entries with and without geographic coordinates.
- Exports:
  - Full substation dataset in CSV format.
  - Separate CSV files for substations with and without coordinates.
  - One GeoJSON file per country containing substations with valid coordinates.

## CSV Files Output

- **`groupedbycountry.csv`**: Lists the total number of substations per country, along with associated types.
- **`wikidata_substations_full.csv`**: Contains all fetched substations including those without coordinates.
- **`wikidata_substations_with_coordinates.csv`**: Contains substations with valid latitude and longitude data.
- **`wikidata_substations_without_coordinates.csv`**: Contains substations missing coordinate information.

## GeoJSON Output

- One GeoJSON file per country is generated inside the geojson_by_country/ directory.
- Each GeoJSON file contains substations with geographic coordinates, suitable to be used as a hint layer for mapping or GIS applications.

## Requirements
To run this script, you need the following Python libraries:
- pandas
- requests
- geopy
- fuzzywuzzy
- scipy
- numpy

You can install all dependencies by running:

pip install -r requirements.txt

## Usage
To run the script, use the following command: python compare_osm_wikidata_powerplants.py.py or python get_wiki_substations.py

**Note**: This project is **under development**. 
