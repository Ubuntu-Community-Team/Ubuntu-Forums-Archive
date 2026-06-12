---
title: "how do you organize playlists?"
date: 2009-07-31
forum: General Help
---

### Post by PGScooter on 2009-07-31
Hi,

I have seen many threads talking about how they organize music. But I have not seen many threads on playlist organization systems.

Here is what I'm thinking of doing:

My music is organized as follows: ~/music/genre/artist/album/trackname.
In the folder "artist" I will have two files: .artistname.m3u and .exclude

.artistname.m3u will contain all of the songs that I know I want in my playlist for that artist. .exclude will have all of the songs that I do not want in my playlist. Why not just move the songs or delete them? maybe I will change my mind in the future, and I would like to keep complete albums. I like the idea of having a .exclude file so that if I want I can always just make a script that goes through and deletes those files or moves them to another folder, only leaving the good stuff behind and the files that I haven't made a decision about yet (see next point).

Those fileslists will be mutually exclusive. Then, I will have a script that goes through and makes a .m3u file of all of the files not in .artistname.m3u or .exclude. These are files that I have not made a decision about and/or have just recently added them to the artist directory. I can then play this playlist when I feel like organizing and triaging the unorganized files.

Then, once I have the playlists at the artistname level, it is easy to make bigger playlists by just combining the smaller ones.

Does this seem unnecessarily complicated?

What do you do?
What do you do with files that you don't want to listen to too often, but still want to keep them around for some reason? Do you just not put them on your main playlists?

Which programs do you use for maintaining/editing your playlists?

---

### Post by PGScooter on 2009-08-02
bump

---

### Post by PGScooter on 2009-08-02
bump

---

### Post by PGScooter on 2009-08-06
bump

---

### Post by bear24rw on 2009-08-06
i just have all my music in one directoy

/media/music/band - song.mp3

---

### Post by martinbaselier on 2009-08-06
I just use banshee to create a list of all my mp3's and if I don't like something I remove it from its multimedia library. If you've got a lot of songs you don't want to hear often, you could use the method you described.

---

### Post by credobyte on 2009-08-06
```
/data/music/song1.mp3
/data/music/song2.mp3
/data/music/song3.mp3

```Software uses something called *Music Library* which is pretty much all I need :)

---

### Post by PGScooter on 2009-08-07
> **credobyte said:**
> ```
/data/music/song1.mp3
/data/music/song2.mp3
/data/music/song3.mp3

```Software uses something called *Music Library* which is pretty much all I need :)

Music Library? I couldn't seem to find this software. Do you have a link?

What about fapg (fast audio playlist generator) -- does anyone use that?

---

### Post by credobyte on 2009-08-07
> **PGScooter said:**
> Music Library? I couldn't seem to find this software. Do you have a link?
 
What about fapg (fast audio playlist generator) -- does anyone use that?
 
Dooh, it's an in-built function for almost all music players. If only Banshee wouldn't be based on Mono ( damn good player/organizer ) :(

---

### Post by arnoutvos on 2011-02-09
i still think itunes (not linux) has the best automatic music organizer. (musiclibrary/artist/album/song)
especially because it keeps the compilations together (musiclibrary/compilations/album/song). i'm still looking for something similar for linux.
i also don't see a good reason why you would organize your music in different folders for every genre. because first of all genres are really subjective and second, you can just fill in the genre in de ID3 tags of mp3. if you do that correctly you can still make playlists in your music player for every genre. there's only 1 problem, i'd like to be able to fill in multiple genres. (e.g. jazz, ambient, female vocalist for 1 song)

---

