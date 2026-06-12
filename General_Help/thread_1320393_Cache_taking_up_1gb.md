---
title: "Cache taking up 1gb"
date: 2009-11-09
forum: General Help
---

### Post by twowheeler on 2009-11-09
I am working on conserving disk space and have followed several howtos in the forums about deleting the apt-get archive, log files, etc.  One question has not been answered.  There is a hidden directory ~/.cache that is over 1GB on my system.  Contents are:

> 
dan@ubuntu:~$ ls -la ~/.cache
total 32
drwxr-xr-x  11 dan users   384 2009-11-07 15:43 .
drwxr-xr-x 120 dan users 11008 2009-11-09 07:16 ..
drwx------   2 dan users  2248 2009-11-09 06:19 compizconfig
-rw-r--r--   1 dan users 12288 2009-11-08 22:30 event-sound-cache.tdb.ec2a5a460b54223d1174360046f55787.i486-pc-linux-gnu
drwx------  28 dan users  7552 2009-11-07 15:45 .fr-l3tTjc
drwxr-xr-x   2 dan users    88 2009-11-07 15:43 gedit
drwxr-x---   2 dan users    48 2009-11-06 22:22 media-art
drwx------   3 dan users    72 2009-02-28 15:17 midori
drwx------   3 dan users    72 2009-11-07 13:40 rhythmbox
drwxr-xr-x   3 dan users    72 2009-11-03 20:22 totem
drwxr-xr-x   2 dan users   392 2009-11-09 06:50 tracker
drwxr-xr-x   2 dan users    80 2008-12-19 06:49 xmms2


The big one is the .fr-l3tTjc directory.  Is it safe to delete this stuff?  This is on ubuntu 9.04.

---

### Post by Giblet5 on 2009-11-09
Disk space is $80/TB... A small cup of two-day-old gas station coffee is worth twice as much as that disk space...

That said, it's safe to remove it, although it will eventually come back again.

Pay attention to free space: having less than 10% free will cause a major slowdown, and running out WILL cause data loss and corruption.

---

### Post by happyhamster on 2009-11-09
The name of the directory suggests it's merely a temporary one, created for example when some data was extracted. So, take a look into that folder to see if you can identify its contents first. 

If not, try moving the folder somewhere else to see if anything breaks.

---

### Post by twowheeler on 2009-11-09
> **happyhamster said:**
> The name of the directory suggests it's merely a temporary one, created for example when some data was extracted. So, take a look into that folder to see if you can identify its contents first. 

If not, try moving the folder somewhere else to see if anything breaks.

Ok thanks.  I moved its contents elsewhere, and everything still works.  All is good.

---

