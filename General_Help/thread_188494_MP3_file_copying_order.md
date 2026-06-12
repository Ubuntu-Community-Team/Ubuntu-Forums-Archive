---
title: "MP3 file copying order"
date: 2006-06-04
forum: General Help
---

### Post by Schapie123 on 2006-06-04
Hi.
I have a Samsung YP-T7 mp3 player. When I copy mp3 files to this player, either with cp or in nautilus, the files get written in exactly the same order as they appear on the hard disk. This causes the player to *not* play them in alphabetical order, which I find very annoying since I often listen to classical music, and I don't like hearing the second part of the first piece, then the fourth of te third piece etcetera.
I have absolutely no experience with bash scripting, but I still tried to look for a solution there. I thought, the dir command shows files in alphabetical order. 
Hence:
```
cp $(dir) /media/mp3player
```
But no luck. When a file contains a space, dir prints a double slash, and cp will fail. With ls, only the space character gets printed, so this won't work either.
And, is there a way to make the same copying script filter out unwanted characters like ':'? I guess vfat can't handle them...

I guess there are lots of people here with more bash scripting experience then I have ;)
Thanks in advance

---

### Post by givré on 2006-06-04
Are you sure it is not simply the order it will be list by your mp3 player itself ? How is it working in windows ?
Anyway, a very bad (but working) solution should be simply to add the track number at the beginning of your files

---

### Post by givré on 2006-06-04
I could only suggest you what is said in this thread
[http://www.ubuntuforums.org/showthread.php?t=188444](http://www.ubuntuforums.org/showthread.php?t=188444)

---

### Post by Schapie123 on 2006-06-04
Thanks for suggesting, but I already have numbered my filenames. And, my mp3 player plays them in the order they appear in it's vfat filesystem. Which cp mimes. I have not the faintest idea how it works in windows, but I don't see why that should bring me any closer to the solution of this problem. I am certain the problem is the copying order, because when I use 'cp -v' (verbose) I see it occuring.
Did you post the right thread in your second reply? I don't see the connection to my problem :)

---

### Post by givré on 2006-06-04
[QUOTE=Schapie123]
Did you post the right thread in your second reply? I don't see the connection to my problem :)[/QUOTE]
You are right man, sorry :cool:

---

