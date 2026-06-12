---
title: "No Windows XP after install ubuntu 10.10"
date: 2011-04-29
forum: General Help
---

### Post by WEBTEK on 2011-04-29
After successfully installing Ubuntu 10.10 in what was an intended side by side install with Windows XP, I can no longer find windows XP. Ubuntu boots up fine though.
 Have I obliterated Windows somehow? New to Linux systems.

Gary Schulz

---

### Post by raja.genupula on 2011-04-29
[https://help.ubuntu.com/community/RestoreGrub](https://help.ubuntu.com/community/RestoreGrub)

---

### Post by linuxyogi on 2011-04-29
Try to find out if you have by mistake formatted or deleted the windows partition.

Boot Ubuntu 

Goto Places

Now there must be the windows partition

if its not there that means you have deleted it

if its there click on it to mount it 

after its mounted, open it & see if the windows files/folders exits or not

If all you can see is a empty  partition you probably have formatted the partition.

---

### Post by trehanabhinav on 2011-04-29
yeah you might have removed xp accidentally
no cure for that

---

### Post by kansasnoob on 2011-04-29
Please post the output of:

```
sudo parted -l
```

---

### Post by WEBTEK on 2011-04-29
I get the following:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  95.9GB  95.9GB  primary   ext4            boot
 2      95.9GB  100GB   4113MB  extended
 5      95.9GB  100GB   4113MB  logical   linux-swap(v1)

Thanks for the reply,

---

### Post by linuxyogi on 2011-04-29
> **WEBTEK said:**
> I get the following:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  95.9GB  95.9GB  primary   ext4            boot
 2      95.9GB  100GB   4113MB  extended
 5      95.9GB  100GB   4113MB  logical   linux-swap(v1)

Thanks for the reply,

You have deleted your windows partition.

Reinstall windows & finally Ubuntu.

Read the installation instructions carefully before installing. Specially the partitioning part.

Good Luck.

---

### Post by daxbau on 2011-04-29
you can also try to install xp on a usb-stick (if you have time up to 20-30h)

then you can use partition table doctor to scan for lost partitions and data...

this could help you to restore lost data (files, documents, and sometimes pictures)

allways read the instructions before doing anything :D

---

### Post by WEBTEK on 2011-04-29
Thanks much. Fortunately I have most everything from Win XP on another computer so I really don't need it that bad. Live and learn I guess.

---

### Post by kansasnoob on 2011-04-29
Maverick's live installer was very buggy, look at posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

If you have data to recover look at TestDisk and PhotoRec:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

With FAT and NTFS partitions I've had a lot of luck with this particular process:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by WEBTEK on 2011-04-30
> **kansasnoob said:**
> Maverick's live installer was very buggy, look at posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

If you have data to recover look at TestDisk and PhotoRec:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

With FAT and NTFS partitions I've had a lot of luck with this particular process:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Kansasnoob,

Many thanks for the links. After briefly looking at posts 1 & 15, I think I see where I might have gone wrong. I'll try this Test Disk procedure and see what happens.

---

