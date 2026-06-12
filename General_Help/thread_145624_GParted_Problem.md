---
title: "GParted Problem"
date: 2006-03-16
forum: General Help
---

### Post by rhomsy on 2006-03-16
I have one ntfs partition on my xp machine, and I tried to repartition it using GParted.  I booted from the ubuntu breezy live cd, and use gparted.  However, when I reduce the size of the partition from 80gig to 25 gig, and then apply the changes, a progress bar comes up, goes away, and then it goes back to the same screen and nothing happens. What's going on.  

I'm trying to reduce the ntsf partition so that I can make two new linux partitions and install ubuntu.

---

### Post by Ramses de Norre on 2006-03-16
I've had nothing but trouble trying to use gparted on ntfs partitions..
I'd shrink the ntfs's in windows first and then use gparted to format the unallocated space.

---

### Post by rhomsy on 2006-03-16
Is there free windows software to do this?

---

### Post by Ramses de Norre on 2006-03-16
It's actually inside windows:)
[http://support.microsoft.com/kb/309000/]("http://support.microsoft.com/kb/309000/")

---

### Post by rhomsy on 2006-03-16
[QUOTE=Ramses de Norre]It's actually inside windows:)
[http://support.microsoft.com/kb/309000/]("http://support.microsoft.com/kb/309000/")[/QUOTE]

No, the disk management utility in XP will allow you delete a partition and create new ones, but it doesn't let you reduce the size of a partition without losing the data on that partition , ala partition magic.  I don't want to buy partition magic though, and gparted doesn't seem to work.

---

### Post by ninjaPants on 2006-03-17
I had the same problem - a two part solution worked for me:

First, only attempt one action at a time.

Second, use the Gparted LiveCD from [here.]("http://gparted.sourceforge.net/livecd.php")

The liveCD is just, well, better. 
Also, the search tool is your friend. [The answer(s) I got to this problem when I had it...]("http://www.ubuntuforums.org/showthread.php?t=134306")

---

### Post by aysiu on 2006-03-17
You may need to ```
sudo apt-get install ntfsprogs
```

Otherwise, if that doesn't work, I recommend [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by plors on 2006-03-17
[QUOTE=ninjaPants]I had the same problem - a two part solution worked for me:

First, only attempt one action at a time.

Second, use the Gparted LiveCD from [here.]("http://gparted.sourceforge.net/livecd.php")

The liveCD is just, well, better. [/QUOTE]

I fully agree, one step at a time is the best and safest approach. Also, since gparted-0.2 a LOT of ntfs-related problems have been solved. It should work for you without any problems. As ninjaPants says it's advisable to use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php").

---

