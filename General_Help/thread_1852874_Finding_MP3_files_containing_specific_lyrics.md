---
title: "Finding MP3 files containing specific lyrics"
date: 2011-10-01
forum: General Help
---

### Post by Kissell on 2011-10-01
I went through the trouble of storing lyrics and cover art inside my MP3 files so that players could display that information during playback.  

Now I want to be able to search that information across my entire collection.  I often know a signature line from a song's chorus, but I have no idea what the artist name or song title are.  I'd like to be able to check every MP3 file I have for that phrase and figure out which song it is I've got stuck in my head.  Yeah, I could google it, but then I wouldn't have an MP3 for the song.  Other reasons would be creating a playlist with all my songs that sing about a particular word or phrase.   

Anyone know anything that can do this in Ubuntu?  I'm comfortable with a command line solution that searches the lyrics of a single file, because I can script that, or just a GUI app, either way...  so long as it doesn't require I manually search each MP3 file's lyrics.

---

### Post by Toz on 2011-10-07
**grep** should be able to do this for you.

```
find . -name "*.mp3" -print0 | xargs -0  grep -i "new orleans"
```
...assuming that the lyrics are embedded in the file.

---

### Post by tgalati4 on 2011-10-07
easytag has searching capability.

---

