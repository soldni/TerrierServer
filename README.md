# TerrierServer
Minimal server for terrier search.

## Running the package

Syntax:

```bash
java [terrier options] -jar terrier-searver-x.x-with-dependencies.jar {hostname} {port}
```

Example (server on `localhost` on port `5000`, terrier files in `/var/terrier-index`, running version `1.0`):

```bash
java -Dterrier.home=/var/terrier-index -jar terrier-server-1.0-jar-with-dependencies.jar localhost 5000
```
By default, server runs on `localhost` on port `4567`.

## Supported Endpoints
 
### `_search` – POST

Used to perform a search. Parameters:

```json 
{
    "query": "",    // put the query string here
    "matchingModelName": "Matching",
    "weightingModelName": "PL2",  // or other models supported by Terriers
    "controls": {
        // add controls here
    },
    "properties": {
        // add properties here
    }
}
```

Response:

```json
{
    "results": [
        {"_id":"clueweb12-1914wb-16-04060", "_score":3.67},
        {"_id":"clueweb12-1914wb-02-33676","_score":3.11}
        // more results after this
    ]
}
```

### `_stats` – GET

This endpoint requires no body. Response:

```json
{
  "fields_lengths": [
    0
  ],
  "documents": 52476,
  "average_length": 834.1046573671774,
  "fields_tokens": [
    0
  ],
  "tokens": 52476,
  "fields": 1,
  "pointers": 13907609,
  "unique_terms": 576447
}
```
