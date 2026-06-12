---
title: "Bad magic number in super-block on all Ubuntu installs"
date: 2010-07-01
forum: General Help
---

### Post by MountainX on 2010-07-01
I've been setting up a number of netbooks for friends in a group I belong to. I recommended and I am installing Ubuntu on all of the netbooks. The netbooks are all identical. Everything has seemed OK until yesterday. I decided to see if I could save time by using dd to clone a completed installation onto an identical HDD. So far I have been installing from a LiveUSB stick.

the way I cloned was
boot from LiveUSB
make sure both HDDs are unmounted
```
dd if=/dev/sda of=/dev/sdc
```
it ran overnight. It copied all the data and reported 0 errors.

After cloning the fresh complete install, I swapped disks and booted with the cloned disk. It booted fine. Then I tried to set the label on the new disk using: # e2label /dev/sda newlabel

The error is **Bad magic number in super-block while trying to open /dev/sda. Couldn't find valid filesystem superblock.**

But the filesystem seems fine. It is mounted. It booted up without errors. But all the e2* tools give the same error.

So I put the original working HDD back in the netbook and booted it up. To my surprise, it gives the same error.

So then I checked another netbook with an identical fresh install of Ubuntu 10.04 32-bit. It gives the same error although the system appears to work fine.

Next I went and checked my own netbook. It is identical except I swapped out the HDD for an OCZ Vertex SSD. I aligned the partitions and prepared that drive carefully. It seems to work great. But when I ran e2label on it I got the same error message.

All the other Ubuntu installs are fresh, clean, standard installs where I let the installer use the whole disk and do the partitioning automatically. All are using ext4. (I put "all variants" in the prefix because I did a fresh install of Linux Mint 9 and it has the same error as Ubuntu 10.04. Kubuntu 10.04 on my desktop gives the same error too.)

All give this error. I suppose the ones I have already shipped to my friends all have this error too.

Is it really an error? Or am I doing something wrong in the process of using the e2fs* tools (tune2fs, e2label, etc.)?

---

### Post by oldfred on 2010-07-01
some links for help:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

Also an odd problem that can appear:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by MountainX on 2010-07-01
Thank you. For some strange reason, ubuntuforums.org wasn't showing new posts for about 10 hours or more... so I couldn't even find my own posts to update them.

Anyway, I resolved this. My problem was the result of my own stupidity and a possibly misleading error message. I was not giving the partition number of the device. I should have been doing e2label /dev/sda1 newlabel

---

