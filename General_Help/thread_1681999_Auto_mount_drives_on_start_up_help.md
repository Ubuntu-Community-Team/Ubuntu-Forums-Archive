---
title: "Auto mount drives on start up help"
date: 2011-02-05
forum: General Help
---

### Post by xdeathcorex on 2011-02-05
I've googled for some tips on how to auto mount drives and the result returns that I have to edit fstab file. I've followed the instruction given but I got confused :p

So anyone can help me edit this thing here?
Here's inside my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a2db9d24-0e18-4f1a-b2ed-8e2c6a83291d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3aec16f2-d6d8-41db-b524-2bc8c952ab75 none            swap    sw              0       0
```

I want to mount sda2 and sda3 on startup so, what's the first step that I have to make here?

---

### Post by ajgreeny on 2011-02-05
Can we see the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
``` please, then it will be easy to tell you what to add.

---

### Post by TeoBigusGeekus on 2011-02-05
Mount your drives with nautilus and post us the output of
```
sudo fdisk -l
```
that's -L
and 
```
blkid
```

EDIT: It never rains answers but it pours... :lolflag:

---

### Post by xdeathcorex on 2011-02-05
Here's** fdisk -l** output.

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdddc6117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10294    82677760    7  HPFS/NTFS
/dev/sda2           10294       12971    21501953    5  Extended
/dev/sda3           12971       38914   208387072    7  HPFS/NTFS
/dev/sda5           10294       12854    20561920   83  Linux
/dev/sda6           12854       12971      939008   82  Linux swap / Solaris

Disk /dev/sdb: 1001 MB, 1001848320 bytes
32 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f4f6dc2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         970      977728+   6  FAT16
```

and here's **blkid**

```
/dev/sda1: LABEL="BODOH" UUID="D270345270344011" TYPE="ntfs" 
/dev/sda3: LABEL="BANGANG" UUID="128CC41A8CC3F5EF" TYPE="ntfs" 
/dev/sda5: UUID="a2db9d24-0e18-4f1a-b2ed-8e2c6a83291d" TYPE="ext4" 
/dev/sda6: UUID="3aec16f2-d6d8-41db-b524-2bc8c952ab75" TYPE="swap" 
```

Sorry, i wanted to mount sda1 and sda3. How? thanks :D

---

### Post by TeoBigusGeekus on 2011-02-05
```
sudo mkdir /media/BODOH /media/BANGANG
```
to create the directories to mount your partitions on.
Then
```
gksu gedit /etc/fstab
```
to edit your fstab file. Add these lines
```
UUID=D270345270344011 /media/BODOH    ntfs defaults 0       0
UUID=128CC41A8CC3F5EF /media/BANGANG  ntfs defaults 0       0
```
to it, save and exit. Reboot and post us about how it went.

---

### Post by glene77is on 2011-02-05
[QUOTE=TeoBigusGeekus;10429828. :lolflag:[/QUOTE]
Teo,
Your signature, I like that about AutoCad.
If my AutoCAD 2000 would run on Linux, 
then I would delete my Windows XP partition. 
Glen Ellis, Memphis, TN

---

### Post by ajgreeny on 2011-02-06
You don't even have to reboot.  After the fstab edit/save, simply run ```
mount -a
```to execute fstab.  If any errors report back here.

---

### Post by TeoBigusGeekus on 2011-02-06
> **glene77is said:**
> Teo,
Your signature, I like that about AutoCad.
If my AutoCAD 2000 would run on Linux, 
then I would delete my Windows XP partition. 
Glen Ellis, Memphis, TN
If your needs can be satisfied by simple and plain Autocad, look at [this]("http://www.bricsys.com/en_INTL/").

EDIT: I'm a cretin - linked brlcad instead of bricscad. Link corrected.

---

### Post by xdeathcorex on 2011-02-06
> **ajgreeny said:**
> You don't even have to reboot.  After the fstab edit/save, simply run ```
mount -a
```to execute fstab.  If any errors report back here.

Now what is this?

```
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

:confused:

---

### Post by dollzii on 2011-02-06
Can't help you much on you're error messages but I've got a tip that has always worked for me. Check out;

ntfs-config

---

### Post by b0b138 on 2011-02-06
Its trying to mount it from your new entries in fstab. But, its saying its already mounted. Do you have either of the ntfs volumes open? If so unmount them then run mount -a. Or just reboot ;)

---

### Post by xdeathcorex on 2011-02-06
> **b0b138 said:**
> Its trying to mount it from your new entries in fstab. But, its saying its already mounted. Do you have either of the ntfs volumes open? If so unmount them then run mount -a. Or just reboot ;)

Hey, I rebooted it and shamwow! It mounted itself :D :D

Thanks guys for all the help, really appreciate it :) :)

---

### Post by b0b138 on 2011-02-06
Oh and on a side note, if you have them mount in /mnt instead of /media they won't show on the desktop. Some people prefer that, but to each their own :D

---

