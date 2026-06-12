---
title: "Used and Free Space Are Wrong on Hard Drive"
date: 2011-03-06
forum: General Help
---

### Post by chris1379 on 2011-03-06
When I look at Filesystem properties, I see

25GB Filesystem
217,629 items totalling 3.8 GB
9.8 GB Used
13.8 GB Free

So I have 3.8 GB of files taking up 9.8GB of space. I know what caused it but not how to fix it. I accidentally let MythTV fill up the drive completely watching live TV. I deleted the files it created but the free space didn't change when I did that. Gparted says it's all OK and so does the Disk Check in Disk Utility. I wanted to make a backup with Clonezilla before I tried anything but I get errors. How do I fix this?

Chris

---

### Post by lithopsian on 2011-03-06
Files always take up more space on disk than their actual size.  Big chunks of disk are allocated so that the file doesn't fragment if it gets a bit bigger one day.  Fragmented files can take up even more space by taking up multiple big chunks of disk even if they are quite small.  I wouldn't worry about it until you start to run short of space.

---

### Post by Topsiho on 2011-03-06
Deleting is not enough. You should also empty the waste bin or whatever it is called on an English system (waste basket?)

As long as it is still there it still takes up space on the hard disk :)

Topsiho

---

### Post by chris1379 on 2011-03-06
I tried to empty the trash but there was nothing in it. I think when the drive was full, the system tried to move files to the trash but couldn't. Now the space is used but not by any files.

The files are orphaned by MythTV I found my answer at
[http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

---

