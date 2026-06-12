---
title: "Script help"
date: 2010-08-15
forum: General Help
---

### Post by redfox1160 on 2010-08-15
I wrote a script that displays the last song I listened to on last.fm:
```
#!/bin/sh
BAND=$(wget -q -O - http://ws.audioscrobbler.com/2.0/user/egross73/recenttracks.xml | grep "</artist>" | head -n 1 | sed -e 's/<[^>]*>//g')
SONG=$(wget -q -O - http://ws.audioscrobbler.com/2.0/user/egross73/recenttracks.xml | grep "</name>" | head -n 1 | sed -e 's/<[^>]*>//g')
echo $BAND '-' $SONG

```
This does what I want it to do, but it is slow. I was wondering if there was a better way to get the source of the website without having to download it with wget.

*On a side note, if you use wmii, I plan on using this to update my status bar with my currently playing last.fm track... i just don't know how to yet!*

---

