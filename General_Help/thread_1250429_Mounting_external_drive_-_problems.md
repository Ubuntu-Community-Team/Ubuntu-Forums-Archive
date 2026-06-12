---
title: "Mounting external drive - problems"
date: 2009-08-26
forum: General Help
---

### Post by growlhero on 2009-08-26
Hi,

I've run into some problems after my PS3 died on me some weeks ago: I can't access the saved game files on my PS3 hdd even when I plug it into OSX/Windows. Now I've tured to Linux to see if there's any way I could access the data in this environment instead.

And yes, I know that Sony says that you can't access it, no matter what you do, but at least I need to try.. Soo..

I plugged in my drive via a SATA - Mini USB adapter, and nothing... Unable to mount location, Can't mount file.. 

So, is there anything I could do? Any way to mount the drive and access the data? Any nitty bitty tricks you guys got up your sleves, cause I can't find anything when googling for a solution.

Cheers

---

### Post by scouser73 on 2009-08-26
Please follow the instructions set out in this tutorial: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by growlhero on 2009-08-26
Trying to mount the drive, information I got from; sudo fdisk -l, with; sudo mount -t vfat /dev/sdb /media/external got me the error:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I know the drive is in Fat32..
Any ideas? Can this be bypassed somehow?

---

### Post by Diabolis on 2009-08-26
Did you see any error messages with:
```
dmesg | tail
```???

As a last option, if you aren't able to mount it, you can recover your files with TestDisk.

---

