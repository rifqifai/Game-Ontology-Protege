# Game-Ontology-Protege
Game merupakan salah satu media teknologi yang banyak digemari masyarakat, mulai dari usia dini hingga orang-orang dewasa. Game selalu menjadi daya tarik sendiri, selain berfungsi sebagai sarana hiburan juga dapat berperan dalam menjalin sarana interaksi dan kompetisi dengan temannya. Penelitian ini bertujuan untuk membuat aplikasi ontologi mengenai game menggunakan protégé 5.5.0. Model ontologi dikembangkan dalam bentuk ontologi dengan struktur hirarki class, tipe class, instance, dan property. Model ontologi yang dihasilkan dapat memberikan informasi dan klasifikasi terhadap masing-masing karakteristik permainan. Dengan demikian dalam menggunakan model ini dapat didefinisikan melalui query yang direpresentasikan ke dalam bahasa SPARQL.

# Diagram Ontologi
![diagram ontologi](https://github.com/rifqifai/Game-Ontology-Protege/blob/master/game.jpg)

# Query menggunakan SPARQL query
1. Tampilkan semua atmosphere yang ada dalam game.
```SQL
SELECT ?atmosphere
WHERE {
?atmosphere rdf:type game:Atmosphere
}
```
2. Tampilkan semua game play yang ada dalam game.
```SQL
SELECT ?gamePlay
WHERE {
?gamePlay rdf:type game:GamePlay
}
```
3. Tampilkan semua genre permainan.
```SQL
SELECT ?genre
WHERE {
?genre rdf:type game:Genre
}
```
4. Tampilkan semua daftar permainan
```SQL
SELECT ?namedGames
WHERE {
?namedGames rdf:type game:NamedGames
}
```
5. Tampilkan semua jenis player
```SQL
SELECT ?numberOfPlayers
WHERE {
?numberOfPlayers rdf:type game:NumberOfPlayers
}
```
6. Tampilkan semua jenis platform permainan
```SQL
SELECT ?platform
WHERE {
?platform rdf:type game:Platform
}
```
7. Tampilkan daftar permainan yang berjenis multiplayer
```SQL
SELECT ?game
WHERE {
?game rdf:type game:NamedGames
FILTER (?NumberOfPlayers >1)
}
```
8. Tampilkan game yang mempunyai atmosphere adventurous
```SQL
SELECT ?game
WHERE {
?game game:hasAtmosphere cake:Adventurous
}
```
9. Tampilkan game yang mempunyai atmosphere aggressive dengan jenis player adalah multiplayer yang memiliki platform dan genre
```SQL
SELECT ?game
WHERE {
?game game:hasAtmosphere cake:Aggressive;
game:hasPlatform ?Platform;
cake:hasGenre ?Genre
cake:hasNumberOfPlayers ?NumberOfPlayers
FILTER (?NumberOfPlayers >1)
}
```
1. Cari game yang bernama GrandTheftAuto
```SQL
SELECT ?subject 
WHERE {
if(!(Atmosphere.equals("GrandTheftAuto")))
queryString += "?subject sw:hasAtmosphere game:" + Atmosphere 
}
```
