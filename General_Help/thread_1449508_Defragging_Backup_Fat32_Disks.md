---
title: "Defragging Backup Fat32 Disks"
date: 2010-04-07
forum: General Help
---

### Post by twilliamswithaz on 2010-04-07
Hey all,
I wasn't completely sure where to post this, as it sort of fit into both the hardware category and the multimedia category (at least, I think so). I hope this is okay.

Anywho, I just installed Ubuntu 8.10, and it's all up to date and such. I've got the OS running on an 8 GB hard drive I swiped from a dead corpse of a computer in my basement, and then I installed two more disks in the case:

160 GB ATA/IDE hard drive
200 GB SATA hard drive.

Both of those hard drives I am using to store media on because this machine is my home samba server (and I found a brilliant HOWTO on these forums, so thanks guys). 

The big issue that I have right now is that BOTH drives are formatted FAT32. I'm pretty sure that because of that fact, those disks will become fragmented at some point? I'd like to be able to defragment them, considering I am streaming movies from them, and seek time is thus fairly critical, since no one likes a laggy movie (I am even getting myself a gigabit switch to help with the new load on my network). 

So my two big questions are:
1) Do I need to defrag? Since the files are going from the disk to samba to my other computers, are they going to be fragmented, still?
2) If I do need to defrag, what tool can I use, and will my files be okay? I REALLY cannot lose some of these files on here (I use it as a backup drive, as well).


As a final note, the 160 GB hard drive is all free space, so if anyone wants to suggest me to format it to ext3 to reduce the need to defrag, feel free to do so. I just really don't want to reformat the 200 GB hard drive, as I would have to back up 60 GB of data I already have on it. 

I hope that wasn't too confusing of a question?

Thanks!

---

### Post by psusi on 2010-04-20
Yes, it will get fragmented, yes, you should reformat to ext3 or 4, and you can try to defrag it with this:

[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

---

### Post by egalvan on 2010-04-20
> **twilliamswithaz said:**
> 
160 GB ATA/IDE hard drive
200 GB SATA hard drive.

 BOTH drives are formatted FAT32. 


**the 160 GB hard drive is all free space**,
 so if anyone wants to suggest me to format it to ext3
 
I just really don't want to reformat the 200 GB hard drive,
 as I would have to **back up [COLOR="Red"]60 GB [/COLOR]of data I already have **on it. 


So format the 160GB to ext3, then back-up the 60g's of data to that first drive...
then **AFTER VERIFYING THE DATA IS SAFE** re-format the second drive.
then copy the 60g's of data back to the original drive.

Also, FAT32 is not the best file system for large drives.
It's ancient technology, designed in the days of 20-100 Megabyte drives.

> 
(I am even getting myself a gigabit switch to help with the new load on my network). 

Unless you are streaming multiple HD streams, then Gigabit is overkill.

BUT... nice to have, and I have it on my network at home... :)

I cold stream three simultaneous  DVD streams without jitter on a 100BaseT.

Upgraded to replace some bad cable segments.

utp is cheap... pulled four strands instead of one, wherever I wanted/needed utp.

It's split into two segments, one for moving large files (music, video, copying, etc) and another for out-bound (Internet) traffic.

The other two are working spares/for redundancy.

but I would suggest an analysis of your LAN and it's topology if you are getting lag.

---

