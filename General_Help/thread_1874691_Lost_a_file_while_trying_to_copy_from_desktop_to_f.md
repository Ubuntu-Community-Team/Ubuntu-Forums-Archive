---
title: "Lost a file while trying to copy from desktop to folder. HOW DO I RECOVER IT?"
date: 2011-11-03
forum: General Help
---

### Post by espritdumal on 2011-11-03
I was trying to put a video from my desktop into a folder but somehow i lost touch of the mouse button and the file dissappeared, how do I recover this file??
Please help me...

---

### Post by Vaphell on 2011-11-03
lost in action during drag and drop? so probably you dropped it on some random directory and moved it there.
If you know its name you can run find command to scan your whole home directory
```
find ~ -iname '*/movie.avi'
```
'*movie*' will find any file that has the string 'movie' anywhere (* = any sequence of chars)

---

