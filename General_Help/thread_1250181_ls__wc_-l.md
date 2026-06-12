---
title: "ls | wc -l"
date: 2009-08-26
forum: General Help
---

### Post by ub007 on 2009-08-26
I've got this directory with a huge number of files of the order ~1.5 million(and continuing to grow).

Theres an app which processes these files and so would decrease the no of files from 1.5 million. if the app doesnt work,the number would increase from the 1.5m. So i need to test whether this app works by making sure that no of files is not growing or size of dir is not increasing.

simple solution is to keep checking number lines using ls *my_dir *|wc -l .But because of the 1.5m + files ls |wc -l takes a long time (hours) to return any output.

du -h takes a while as well.

Can someone suggest a work around for this?

---

### Post by DaithiF on 2009-08-26
Hi,
the first thing I would try would be ls -U  (unsorted) rather than ls.  Sorting 1.5million files is going to take a long time!

I would guess that should give you a big enough speed-up.  If not, maybe tackle it from the opposite direction -- log the files which your app processes, and monitor that list to make sure it **growing**.  Up until the half-way point it'll be a shorter list!

---

### Post by danwood76 on 2009-08-26
Or the other alternative is to re think the way you are processing these things and why you need 1.5m files in one directory.

You could also change filesystem to speed things up.
EXT4 has much faster access times than EXT3 as an example.

---

### Post by Aubergines on 2009-08-26
This has really stumped me. I don't think there's any way of speeding up "ls" or "du" simply because they go through every file and is probably limited to IO. But just thinking out loud, "df" get it's information from the superblock and is much faster than "du". If you mounted a separate partition in the directory you should be able to monitor it using "df".

---

### Post by ub007 on 2009-08-26
> Or the other alternative is to re think the way you are processing these things and why you need 1.5m files in one directory.

You could also change filesystem to speed things up.
EXT4 has much faster access times than EXT3 as an example. 

These are set,it would be hard to convince the design folks to change few things for the convenience of my monitoring,..hence i'm not even thinking in that direction at the moment..

> maybe tackle it from the opposite direction -- log the files which your app processes, and monitor that list to make sure it growing. Up until the half-way point it'll be a shorter list! 

Could you plz elaborate a bit more on how to do that

---

### Post by DaithiF on 2009-08-26
for what its worth, i did a quick test of ls vs ls -U on a directory with 250,000 files.  The unsorted version ran 5 times faster.  So if you haven't tried that yet I'd suggest you do.

As for the other suggestion, its hard to be specific without knowing what the app that processes these files is doing, but the idea would be to write out to a logfile the name of each file that is processed.  Your monitor process can do a simple wc -l of that logfile to count the files processed.

---

### Post by lykwydchykyn on 2009-08-26
find might also be faster, I can't say for sure.

find . |wc -l

---

