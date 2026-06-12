---
title: "batch: search movie rating and sort"
date: 2012-02-13
forum: General Help
---

### Post by JohnnyC35 on 2012-02-13
I am looking for a program or script or something... to be able to sort a directory of movies into directories for ratings,
 So some movies would go into G, PG, PG13, etc. I have tried Googling and  using Synaptic but haven't found a program to do what I want, and doing  it by cli is a little beyond me. Any help would be great :smile:

---

### Post by Vaphell on 2012-02-13
if you got the list of titles and categories in a tidy format then it should be doable, if we are talking about querying some internet database, dealing with title duplicates, ambiguities and scraping the data off webpages... then it belongs to the 'world of pain' category.

---

### Post by JohnnyC35 on 2012-02-13
I have a bunch of tidy titled filenames in one large directory. I imagine that it would be needed to access some database to find the ratings but other than that ummm... ya... :confused:

script wise...
imdb.com/search=filename (minus the last 4 characters)
find the character (x) after 'rating: '
move file into /movies/x

..  think it may be a bit more complicated than that

---

### Post by Vaphell on 2012-02-13
main problem is that movie titles are not unique and imdb presents you with disambiguation pages more often than not. You have to manually select the right entry.
'titanic' gives you like dozen results

---

### Post by HiImTye on 2012-02-13
you could just use XBMC, it has plugins to manage TV Show and Movie information, from TVDB, TheMovieDB, IMDB, etc

---

### Post by JohnnyC35 on 2012-02-13
> **HiImTye said:**
> you could just use XBMC, it has plugins to manage TV Show and Movie information, from TVDB, TheMovieDB, IMDB, etc

I see in XBMC there are addons to get movie info, but it doesn't list it in the directory listing or have an option to list by rating :(

---

### Post by HiImTye on 2012-02-13
you can sort your movies by rating, when youre in your movie browser, go to the left side of the screen so that the menu pops out and then change the 'sort by:' setting until it says 'MPAA Rating'

---

### Post by JohnnyC35 on 2012-02-14
> **HiImTye said:**
> you can sort your movies by rating, when youre in your movie browser, go to the left side of the screen so that the menu pops out and then change the 'sort by:' setting until it says 'MPAA Rating'

I have 'TheMovieDb' and 'IMDb' enabled under movie information and when I check 'sort by:' I don't see 'MPAA Rating'. What addon do I need to be able to have that option? I have whatever version of XBMC comes with their repo. My options are by Date, File, Name, or Size.

---

