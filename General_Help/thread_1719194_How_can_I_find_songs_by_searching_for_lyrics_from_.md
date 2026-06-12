---
title: "How can I find songs by searching for lyrics from musics I own"
date: 2011-04-01
forum: General Help
---

### Post by metalf8801 on 2011-04-01
I need suggestions for the best way(s) to download song lyrics for CDs and Records that I own and then be able to search those lyrics later when I forget the name of a song, but I can remember some of the lyrics. So searching for the name of lyrics file isn't going to be enough I need to be able to search the text in the file. 

I know I can use the Rhythmbox Song Lyrics plugin to download lyrics for most of my music (at least for my CDs and ogg files). Although it would be nice if it did a better job of telling me when it couldn't find lyrics to a song. So if anyone has a better solution please tell me. 

While I can use online lyrics search engines they have to many songs in them, but they don't always have all of the songs I own. So that really doesn't solve my problem. 

I'm open to any suggestions 

Thank you 
Dan

---

### Post by aromo on 2011-04-01
Copy the lyrics you are interested in to a folder in your hdd.  Each file will be a song.  You can organize them in folders, for instance:
/lyrics
/lyrics/artist1
/lyrics/artist1/album1
/lyrics/artist1/album1/song1.txt
/lyrics/artist1/album1/song2.txt
/lyrics/artist1/album2
/lyrics/artist2
/lyrics/artist2/album1
/lyrics/artist2/album2

Then you run:
grep -rl "part of the lyrics" /lyrics

This will show you the file names (including path) containing the partial lyrics.  If you followed my example, you'll get the artist, album and song name.

Hope this helps.

---

### Post by metalf8801 on 2011-04-01
> **aromo said:**
> Copy the lyrics you are interested in to a folder in your hdd.  Each file will be a song.  You can organize them in folders, for instance:
/lyrics
/lyrics/artist1
/lyrics/artist1/album1
/lyrics/artist1/album1/song1.txt
/lyrics/artist1/album1/song2.txt
/lyrics/artist1/album2
/lyrics/artist2
/lyrics/artist2/album1
/lyrics/artist2/album2

Then you run:
grep -rl "part of the lyrics" /lyrics

This will show you the file names (including path) containing the partial lyrics.  If you followed my example, you'll get the artist, album and song name.

Hope this helps. 
Thank you that works. However, I'm still open to other suggestions if anyone has any.

---

