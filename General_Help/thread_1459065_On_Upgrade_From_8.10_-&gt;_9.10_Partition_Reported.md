---
title: "On Upgrade From 8.10 -&gt; 9.10 Partition Reported as '110 GB Extended' (Label Ignored)"
date: 2010-04-20
forum: General Help
---

### Post by Synthdark on 2010-04-20
In 8.10 Ubuntu reported sda5 as 'Data' (the partition label). After the upgrade to 9.10 Ubuntu now reports the partition as '110 GB Extended' (NOT the partition label). This is only happening to the extended partition, sda1 is correctly reported as 'XP'.

Is this a bug or was the behavior changed? How can I get Ubuntu to report the partition as 'Data' again?

```
fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3107    24956946    7  HPFS/NTFS
/dev/sda2            3108        4523    11374020   83  Linux
/dev/sda3            4524        4772     2000092+  82  Linux swap / Solaris
/dev/sda4            4773       19457   117957262+   f  W95 Ext'd (LBA)
/dev/sda5            6078       19457   107474818+   7  HPFS/NTFS

blkid
/dev/sda1: UUID="42D0E397D0E38F89" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="6c823a00-4244-485a-85a1-2d936c2e3110" TYPE="ext3" 
/dev/sda3: UUID="55eade65-50e0-44b7-afa8-650f2de1ae23" TYPE="swap" 
/dev/sda5: UUID="9E6C10C46C10995B" LABEL="Data" TYPE="ntfs"
```

Ubuntu 9.10 x86-32   Inspiron 600m

Let me know if any other info is needed & I'll add it.

---

### Post by darolu on 2010-04-20
What do you mean by "reports" it as 110GB extended?
```
/dev/sda5: UUID="9E6C10C46C10995B" **LABEL="Data"** TYPE="ntfs"
```
I see BLKID reports it as "Data".

---

### Post by Synthdark on 2010-04-20
Nautilus (Gnome) shows the partition as '110 GB Extended' instead of 'Data'. (the desktop icon, drive listed in computer:///, etc.)

I now remember that Ubuntu != Nautilus, this had slipped my mind. Sorry for the confusion.

---

### Post by darolu on 2010-04-20
The names displayed in Nautilus (its left panel, under places and the desktop) are taken from the contents on /media/; to get the names you want you will need to edit your /etc/fstab file; I'm unsure why the 'XP' partition is mounted as 'XP' though.

Can you please post the contents of your fstab file? Open a terminal (Applications - Accessories - Terminal) or press Alt+F2 and run this command:
```
gksudo gedit /etc/fstab
```
The use of gksudo is actually not necessary to display the contents of your fstab file, but it is necessary should you need to edit it.

---

### Post by Synthdark on 2010-04-21
The XP partition is shown as XP 'cause I altered fstab to mount it as such; same with the Data partition. I'm just not sure why it stopped working. I think it has something to do with it being within an extended partition, bit I'm not sure.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6c823a00-4244-485a-85a1-2d936c2e3110 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=9E6C10C46C10995B       /media/Data     ntfs    defaults,umask=0000,uid=1000,fmask=0000,dmask=0000 0       0
# /dev/sda1
UUID=42D0E397D0E38F89 /media/XP     ntfs    defaults,umask=0007,uid=1000,fmask=0007,dmask=0007 0       0
# /dev/sda3
UUID=55eade65-50e0-44b7-afa8-650f2de1ae23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

The only major difference between the two partitions and how they are mounted is that one in within an extended partition (Data) and the other is not (XP).

---

### Post by Synthdark on 2010-04-22
Shameless Bump

---

### Post by darolu on 2010-04-22
> /home/media/Data    ntfs
Try mounting them to /media/, that should do the trick:
```
UUID=9E6C10C46C10995B       **/media/Data     ntfs-3g**    defaults,umask=0000,uid=1000,fmask=0000,dmask=0000 0       0
```
Remember, you have to create the mount point first (sudo mkdir /media/Data) I also recommend using ntfs-3g instead of ntfs as ntfs-3g gives writting capabilities.

---

### Post by Synthdark on 2010-04-22
I can't believe I missed the /home heh

The actual mount points are /home/gregory/.XP & /home/gregory/.Data
I've left symlinks in /media (as: /media/XP & /media/Data). I did this ages ago (wile I was still learning about linux) to prevent anyone else on the system from accessing the drives and just never got around to changing it & left symlinks so they'd show up on the desktop.

As far as Nautilus is concerned it should only be seeing /media/XP & /media/Data as the mounted partitions.

Anyways, for the purposes of testing I mounted the Data drive as /media/Data1 (brand new folder) but it still shows up as '110 GB Extended'.

Why is ntfs-3g needed for writing? They aren't read-only, I can write as much as I want.


Edit: Changing it to ntfs-3g didn't help, it's still being displayed as '110 GB Extended'.

---

### Post by darolu on 2010-04-22
As of why ntfs-3g: [http://en.wikipedia.org/wiki/NTFS-3G](http://en.wikipedia.org/wiki/NTFS-3G)
I have my 2 ntfs partitions set this way (in /media/<label>) and work fine, I'm not sure why it isn't working for you.

---

