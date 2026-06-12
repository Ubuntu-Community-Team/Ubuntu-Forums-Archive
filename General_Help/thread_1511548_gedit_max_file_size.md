---
title: "gedit max file size?"
date: 2010-06-17
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-06-17
so i opened a 204kb js file (prefs.js)
needed a settings from my windows partition's firefox
i scrolled down and gedit locked up
i tried it in wine notepad
it crashed where gedit locked up
wine notepad++
lagged there but i was able to get it
what is the limit on it
system specs in signature

---

### Post by anglican on 2010-06-17
> **pqwoerituytrueiwoq said:**
> so i opened a 204kb js file (prefs.js)
needed a settings from my windows partition's firefox
i scrolled down and gedit locked up
i tried it in wine notepad
it crashed where gedit locked up
wine notepad++
lagged there but i was able to get it
what is the limit on it
system specs in signature
I'm not sure what the file size limit on gedit is but I'm certain it should handle 204K without difficulty. If you want to try an alternative editor that definitely does have large file support (i.e. > 4GB) you could try gvim.

H

---

### Post by Chesamo on 2010-06-17
I know GEdit has no such filesize restriction; on that note, no editor should lock up with 240k of data. Try opening it in nano (a command-line text editor) and see what happens.

---

### Post by pqwoerituytrueiwoq on 2010-06-17
nano lagged (processor usage jumped up about 10%) at that point but when it got pasts it it quit lagging
i tried gedit again and scrolled quickly
maybe there are too may characters on a single line
the longest line is 132899 characters long. Long json, it is used like a database by a greasemoneky scripts
gvim handled it as good as nano did

---

### Post by RTrev on 2010-06-17
> **pqwoerituytrueiwoq said:**
> 
the longest line is 132899 characters long.


Oh wait, my mistake.. edited to correct mis-reading.

I'm not sure I've ever had a line that long.  Is there a reason it can't be broken into smaller chunks?

---

### Post by pqwoerituytrueiwoq on 2010-06-17
not with out reprogramming a script 
the file is not meant to be edited manually like that i just did not feel like rebooting to windows to get something that i know where it is it a plain text file and that line just happened to be there
i was just wondering why it locked up

---

