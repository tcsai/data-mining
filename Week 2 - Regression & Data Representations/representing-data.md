## Representing Data

![img](./img/influ.png)

**Practical Lectures** <br>
by Chris Emmery (MSc) <br>
[`@_cmry`](https://twitter.com/_cmry) &nbsp; • &nbsp; [`@cmry`](https://github.com/cmry)

<style>
body {
	color: #aaa;
}
</style>


### Last Week

- Data
- Features
- Algorithms


### This Week

- Data ←
- Features
- Algorithms


### How do we get Data?

- Pre-mades: e.g. [Kaggle](https://www.kaggle.com), [UCI](https://archive.ics.uci.edu/ml/datasets.html), [Snap](https://snap.stanford.edu/data/).
- Dumps: e.g. [IMDB](http://www.imdb.com/interfaces), [Reddit](https://files.pushshift.io/reddit/comments/), [MovieLens](https://grouplens.org/datasets/movielens/).
- Scientific repositories: e.g. [dataverse](https://dataverse.nl/).
- [(Web) API](https://en.wikipedia.org/wiki/Web_API)'s: e.g. [Twitter](https://dev.twitter.com/overview/api), [Reddit](https://www.reddit.com/dev/api).
- Web scraping.
- At industry-level: databases.



## File Formats

![rosetta](./img/rosetta.png)


### How is data formatted?

- **CSV** → flat (table format), named columns and rows. Separators and quotes.
- **JSON** → hierchical, lists and key/values. Widely used for API's and document-based databases.
- **XML** → hierchical, tags to name items. Very common standard; easy to evaluate if according to some pre-defined structure.


### CSV - Object

![tweet](./img/house.jpg)

(for sale)


### CSV - File

``` csv
CRIM,ZN,INDUS,CHAS,NOX,RM,AGE,DIS,RAD,TAX,PTRATIO,B,LSTAT,MEDV
0.00632,18.00,2.310,0,0.5380,6.5750,65.20,4.0900,1,296.0,15.30,396.90,4.98,24.00
0.02731,0.00,7.070,0,0.4690,6.4210,78.90,4.9671,2,242.0,17.80,396.90,9.14,21.60
0.02729,0.00,7.070,0,0.4690,7.1850,61.10,4.9671,2,242.0,17.80,392.83,4.03,34.70
0.03237,0.00,2.180,0,0.4580,6.9980,45.80,6.0622,3,222.0,18.70,394.63,2.94,33.40
```

| CRIM    | ZN    | INDUS | CHAS | NOX    | ... |
| ------- | ----- | ----- | ---- | ------ | --- |
| 0.00632 | 18.00 | 2.310 | 0    | 0.5380 | ... |
| 0.02731 | 0.00  | 7.070 | 0    | 0.4690 | ... |
| 0.02729 | 0.00  | 7.070 | 0    | 0.4690 | ... |
| 0.03237 | 0.00  | 2.180 | 0    | 0.4580 | ... |


### JSON - Object

![tweet](./img/tweet.png)


### JSON - File

``` json
[{
  "created_at": "Thu Jun 22 21:00:00 +0000 2017",
  "id": 877994604561387500,
  "id_str": "877994604561387520",
  "text": "Creating a Grocery List Manager Using Angular, Part 1: Add &amp; Display Items https://t.co/xFox78juL1 #Angular",
  "truncated": false,
  "entities": {
    "hashtags": [{
      "text": "Angular",
      "indices": [103, 111]
    }],
    "symbols": [],
    "user_mentions": [],
    "urls": [{
      "url": "https://t.co/xFox78juL1",
      "expanded_url": "http://buff.ly/2sr60pf",
      "display_url": "buff.ly/2sr60pf",
      "indices": [79, 102]
    }]
  },
  "user": {
    "id": 772682964,
    "id_str": "772682964",
    "name": "SitePoint JavaScript",
    "screen_name": "SitePointJS",
    "location": "Melbourne, Australia",
    "description": "Keep up with JavaScript tutorials, tips, tricks and articles at SitePoint.",
    "url": "http://t.co/cCH13gqeUK",
    "entities": {
      "url": {
        "urls": [{
          "url": "http://t.co/cCH13gqeUK",
          "expanded_url": "http://sitepoint.com/javascript",
          "display_url": "sitepoint.com/javascript",
          "indices": [0, 22]
        }]
      },
      "description": {
        "urls": []
      }
    },
    "protected": false,
    "followers_count": 2145,
    "friends_count": 18,
    "listed_count": 328,
    "created_at": "Wed Aug 22 02:06:33 +0000 2012",
    "favourites_count": 57,
    "utc_offset": 43200,
    "time_zone": "Wellington",
  },
}]
```

``` python
tweet['text'] = "Creating a Grocery List Manager ..."
tweet['entities']['hashtags'][0]['text'] = "Angular"
tweet['user']['screen_name'] = "SitePointJS"
```


### XML vs JSON

```xml
<?xml version="1.0"?>
<book id="123">
  <title>Object Thinking</title>
  <author>David West</author>
  <published>
    <by>Microsoft Press</by>
    <year>2004</year>
  </published>
</book>
```
```json
{
  "id": 123,
  "title": "Object Thinking",
  "author": "David West",
  "published": {
    "by": "Microsoft Press",
    "year": 2004
  }
}
```



## Databases

![data](./img/data.png)


### What are Databases?


### (Non) Relational

- **SQL**: e.g. [MySQL](https://www.mysql.com/), [PostgreSQL](https://www.postgresql.org/), [SQLite](https://sqlite.org/), [MariaDB](https://mariadb.org/).
  - Pre-defined, structured, relational → not easy to scale horizontally, but robust, and well-supported.
- **NoSQL**: e.g. [MongoDB](https://www.mongodb.com/), [CouchDB](https://couchdb.apache.org/), [Cassandra](https://cassandra.apache.org/), [Redis](https://redis.io/).
  - Flexible, multiple designs, not (only) relational → automatic and easy scalability, many different varieties, upcoming thus less well supported.


### SQL

```sql
CREATE TABLE STATION
(ID INTEGER PRIMARY KEY,
CITY CHAR(20),
STATE CHAR(2),
LAT_N REAL,
LONG_W REAL);
```

```sql
INSERT INTO STATION VALUES (13, 'Phoenix', 'AZ', 33, 112);
INSERT INTO STATION VALUES (44, 'Denver', 'CO', 40, 105);
INSERT INTO STATION VALUES (66, 'Caribou', 'ME', 47, 68);
```

```sql
SELECT CITY, STATE FROM STATION WHERE LAT_N > 39.7;
```

| CITY    |	STATE |
| ------- | ----- |
| Denver  | 	CO  |
| Caribou | 	ME  |


### NoSQL

```javascript
db.station.insertMany([
  {"id": 13,
   "city": "Phoenix", "state": "AZ",
   "lat_n": 33, "long_w": 112},
  {"id": 44,
   "city": "Denver", "state": "CO",
   "lat_n": 40, "long_w": 105},
  {"id": 66,
   "city": "Caribou", "state": "ME",
   "lat_n": 47, "long_w": 68}
])
```

```javascript
db.station.find({"lat_n": {$gt: 39.7}},
                {"city": 1, "state": 1})
```

| CITY    |	STATE |
| ------- | ----- |
| Denver  | 	CO  |
| Caribou | 	ME  |


## Representing Data and Knowledge

![trinity](./img/trinity.png)


### Analysis vs. Predictive Analysis

- 80% analysis: collecting, discovering, cleaning and aggregating data
  from different databases / sources to generate creative insights.
- 20% prediction: use all the above to generate insights only possible by
  machines.


### Example of Manual Analysis

What's in a Tweet?

- Text (hashtags, urls, mentions, emojis)
- Users (images, names, descriptions, links)
- Time
- Location
- Networks (reach, spread)

> All directly in human readable data.


### How do we represent data for machines?

| rating | actor     | year | label     |
| ------ | --------- | ---- | --------- |
| 6.5    | johansson | 2017 | okay      |
| 7      | pitt      | 2013 | good      |
| 8      | doubleday | 2015 | very good |


### Representation: Regression

$$ X =
  \begin{bmatrix}
  1 & 2016 & 3 \newline
  0 & 2014 & 4 \newline
  6 & 2012 & 5
  \end{bmatrix}
$$

$$ Y =
  \begin{bmatrix}
  6.5\newline
  7.0\newline
  8.0
  \end{bmatrix}
$$


### Representation: Classification

$$ X =
  \begin{bmatrix}
  6.5 & 1 & 2016\newline
  7.0 & 0 & 2014\newline
  8.0 & 6 & 2012
  \end{bmatrix}
$$

$$ Y =
  \begin{bmatrix}
  3\newline
  4\newline
  5
  \end{bmatrix}
$$


### Vector Spaces

$$
\begin{matrix}
\vec{x_1} = \langle 6.5, 1, 2016 \rangle \newline
\vec{x_2} = \langle 7.0, 0, 2014 \rangle \newline
\vec{x_3} = \langle 8.0, 6, 2012 \rangle
\end{matrix}
$$



## Questions?

> Blackboard → Forum
