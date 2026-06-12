---
title: "Weirdness trying to figure out directory size"
date: 2010-03-06
forum: General Help
---

### Post by Donny Bahama on 2010-03-06
I did  a search, and it looks like 'du' is what I'm supposed to use to figure out how big a directory (and all the files and subdirs it contains) is. So I ran ```
du-sh ./donny
``` (on my home directory) and it returned:
```
du: cannot read directory `./donny/.dbus': Permission denied
13G    ./donny
```Presumably, "13G" is the answer I'm looking for, but when I bring it up in Nautilus and right-click my home folder and choose properties, it says:```
251 items, totalling 2.9 GB
```Everywhere I've searched, it says to use du for getting a directory size, but I can't seem to get it to return the correct value. What am I doing wrong?

---

### Post by Fir3chi3f on 2010-03-06
There should be a space in the first line of code you posted:
```
du -sh
```

If you just run the above^ code in the terminal without anything else it should search your home directory. Your terminal starts out in your home folder.

Is your home directory hidden? A dot infront of the folder path usually indicates a hidden folder.

Thought I did notice a bit of a difference when I ran it as well. 

du -sh indicates 22G

Folder properties indicates 24.1G

---

### Post by Donny Bahama on 2010-03-06
> **Fir3chi3f said:**
> There should be a space in the first line of code you posted
Thanks for the response! I did put a space in when I ran it in the terminal. That was just a typo when I posted.
> Is your home directory hidden? A dot infront of the folder path usually indicates a hidden folder.No, not hidden.

---

