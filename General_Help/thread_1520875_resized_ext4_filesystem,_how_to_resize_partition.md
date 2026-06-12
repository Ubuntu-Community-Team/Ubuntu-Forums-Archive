---
title: "resized ext4 filesystem, how to resize partition ?"
date: 2010-06-30
forum: General Help
---

### Post by alesserfate on 2010-06-30
hey folks,

i'm resizing an ext4 partition from 100gb to 40gb (i only used 20gb of it or so)

lets say partition is at /dev/sda1

i used ```
efsck -f /dev/sda1
``` to check it

then i did ```
resize2fs -p /dev/sda1 40G
``` to resize it

when i check fdisk -l, the partition is still 100gb

i have a feeling I resized ONLY the filesystem to 40, but the partition is still 100gb

how do i finish this ?

lmk thanks!!!!!!!!!!!!!1111111111111

---

### Post by gzarkadas on 2010-06-30
Use gparted. It is a GUI partition editor, accessible from the menu `System|Administration|Gparted'. If not installed fireup Synaptic Package Manager (from the same menu) to install it.

---

### Post by bumanie on 2010-06-30
+1 for gparted - here's a [tutorial]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html") if you have problems. Remember it is always best to back important stuff before doing something like partitioning, although it usually works without a problem.

---

### Post by dino99 on 2010-06-30
do it with partition not mounted, its important. Better to boot with a cd and partedmagic on it to resize your partitions

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by alesserfate on 2010-07-01
just confirmed filesystem size is 40gig, partition size is 100gig

i am forever in runlevel 3, should I still bother with gparted ?

---

### Post by bodhi.zazen on 2010-07-01
> **alesserfate said:**
> just confirmed filesystem size is 40gig, partition size is 100gig

i am forever in runlevel 3, should I still bother with gparted ?


Now that you have gone this far, finish it off =)

It would take more time to boot the live CD.

See :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

It is written for encrypted partitions, but it is far easier with un encrypted partitions as you do not have to manage LVM or the crypt :p

Next time though, you may with to use gparted.

---

### Post by alesserfate on 2010-07-07
> **bodhi.zazen said:**
> Now that you have gone this far, finish it off =)

It would take more time to boot the live CD.

See :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

It is written for encrypted partitions, but it is far easier with un encrypted partitions as you do not have to manage LVM or the crypt :p

Next time though, you may with to use gparted.

Thank you kind sir, partition resized successfully, it's been a while since I was hitting up terminal hardcore.

---

### Post by ario on 2010-10-30
> **alesserfate said:**
> Thank you kind sir, partition resized successfully, it's been a while since I was hitting up terminal hardcore.

Ok. Can you please let us know which commands you used to do this?
I already know e2fsck and resize2fs steps. The next step is a black magic which I can't find on the Internet.
I do not want to use gparted. Because it's many years since we people telling them to add a progress bar for resize situation and they say we have not enough time to do so!
So which commands I must run after the resize2fs -p /dev/sdaX ?

---

### Post by ario on 2010-11-01
Bump!

---

### Post by bodhi.zazen on 2010-11-02
> **ario said:**
> Bump!

No offense, but did you read the wiki ?

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

I believe the next step is

e2fsck -f

---

### Post by ario on 2010-11-03
> **bodhi.zazen said:**
> No offense, but did you read the wiki ?

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

I believe the next step is

e2fsck -f

Will try that on a virtual machine.

---

