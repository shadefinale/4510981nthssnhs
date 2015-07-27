Run queries on the `tutorial.billboard_top_100_year_end` database on the [Mode Analytics editor](https://modeanalytics.com/editor).

1. How many years did Mariah Carey have a song in the Top 10?
SELECT count(*)
FROM tutorial.billboard_top_100_year_end
WHERE year_rank < 10 AND artist ilike '%mariah carey%'

2. A list of all Whitney Houston song titles that didn't rank higher than 20th, in chronological order.
SELECT song_name
FROM tutorial.billboard_top_100_year_end
WHERE artist ilike '%Whitney Houston%' AND year_rank >= 20
ORDER by year asc


3. How many artists have finished a year with the number 1 song?
SELECT count(DISTINCT artist)
FROM tutorial.billboard_top_100_year_end
WHERE year_rank = 1

4. In which year did Ke$ha have the most charted hits, and how many did she have that year? (Just one query...)
SELECT count(*), year
FROM tutorial.billboard_top_100_year_end
WHERE artist ilike '%Ke$ha%'
GROUP BY year
ORDER BY 1 DESC



5. What is the highest chart position ever reached by Ke$ha's sometime collaborators, the strangely-named "3OH!3"?
SELECT MAX(year_rank)
FROM tutorial.billboard_top_100_year_end
WHERE "group" ilike '%3OH!3%'


6. A list of years that had a charted song containing the word "heaven" and a count of the number.
SELECT count(*), year
FROM tutorial.billboard_top_100_year_end
WHERE song_name ilike '%heaven%'
GROUP BY year
