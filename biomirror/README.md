# BioMirror / Literature Mirror

A programmatically created catalog of biomedical knowledge, tools, and materials.

## Project Vision

The goal of this project is to create a comprehensive meta-data catalog of the world's biomedical literature, tools, and materials.
Eventually, this catalog will include:

* An index of biocontainer tools and their metadata
* A database of biomedical literature from PMC and PubMed
* Relevant AI weights.
* Public and private cohorts of well-consented human beings in which biomedical claims can be validated and biomedical tools can be benchmarked.

These resources will be aggregated using automated pipelines into a browseable format that can be updated at periodic intervals.

## Current Milestone (Phase 1)

As a starting point, we are building a foundation to ingest metadata from Europe PMC and PubMed, convert it into a SQLite database using a python script, and allow browsing/searching of the catalog from a web page using JavaScript. cf. [GitHub Pages](https://sherawz.github.io/literature-tools-catalog/)

We are currently working with the PMID <> PMCID <> DOI map downloaded from EuropePMC.

### TODOs

1. Implement advanced client-side database querying techniques (like HTTP Range requests for partial database loading) to handle extremely large datasets without overwhelming the browser.
2. Make the front-end pageable so that we can potentially visit all 400,000 (or 40m entries.)

## Full Project Plan

### Phase 1: Foundation and Initial Ingestion (Current)

1. **Data Ingestion**:
   * Parse the initial dataset (`PMID_PMCID_DOI.csv`) containing PMID, PMCID, and DOI mappings.
   * Create a python script to read this CSV and populate a local SQLite database.
2. **Data Processing and Indexing**:
   * The python script outputs a well-indexed `catalog.db` optimized for querying.
3. **Frontend Web Interface**:
   * A static web page with JavaScript that loads and queries the SQLite database on-demand using range requests through the library [sql.js-httpvfs](https://github.com/phiresky/sql.js-httpvfs).
   * Enables users to performantly search the catalog entirely client-side, reducing server infrastructure needs.

### Phase 2: Comprehensive Metadata Enrichment

* Expand the ingestion program or create additional scripts to fetch additional metadata (titles, authors, abstracts, publication dates) from Europe PMC and PubMed APIs for the ingested IDs.
* Update the SQLite schema to store and index this enriched metadata.
* Enhance the frontend search capabilities to support text-based searches on titles and abstracts.

### Phase 3: Tools and Materials Integration

* Define schemas for biomedical tools and materials.
* Implement ingestion pipelines for tool repositories and material catalogs.
* Update the user interface to support faceted search across literature, tools, and materials, linking them where applicable.

### Phase 4: AI Weights and Human Cohorts

* Expand the database to catalog relevant AI models and their weights.
* Integrate metadata for public and private human cohorts (ensuring appropriate consent and privacy standards are modeled in the metadata).
* Provide advanced querying to connect literature claims and tool benchmarks to specific human cohorts.

### Phase 5: Scale and Automation

* Automate the ingestion pipelines to keep the catalog up-to-date with the latest publications and releases.
* Optimize the database generation process and indexing for scale.
