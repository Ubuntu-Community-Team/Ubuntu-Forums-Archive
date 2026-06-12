---
title: "Access windows partitions in ubuntu 10.10"
date: 2010-11-09
forum: General Help
---

### Post by JBark1 on 2010-11-09
[FONT=Calibri][SIZE=3]I’m completely new to Linux. Now, I have just installed Ubuntu 10.10 along with Windows XP but cannot boot up the last one. In addition, I’m unable to access some very important files stored on the (D:) partition of my hard drive.

Do I first have to mount these partitions in order to get access and how?

Thank you! [/SIZE][/FONT]

---

### Post by Verbeck on 2010-11-09
how did you install ubuntu?wubi or partitioned dualboot?

normally, the partitions should be listed under the places menu

---

### Post by JBark1 on 2010-11-09
I've just downloaded the Ubuntu Desktop Edition and chose install along wih Windows XP. Btw, they're not visible under my places.

---

### Post by JBark1 on 2010-11-09
> **Verbeck said:**
> how did you install ubuntu?wubi or partitioned dualboot?
 
normally, the partitions should be listed under the places menu
 
I've just downloaded the Ubuntu Desktop Edition and chose install along wih Windows XP. Btw, they're not visible under my places.

---

### Post by Verbeck on 2010-11-09
could you post the output of the following command from a terminal (Applications>accessories>terminal)
```
sudo fdisk -l
```

---

### Post by JBark1 on 2010-11-10
> **Verbeck said:**
> could you post the output of the following command from a terminal (Applications>accessories>terminal)
```
sudo fdisk -l
```

Here's the output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00082bbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18895   151768064   83  Linux
/dev/sda2           18895       19458     4519937    5  Extended
/dev/sda5           18895       19458     4519936   82  Linux swap / Solaris

---

### Post by I'mGeorge on 2010-11-10
try disk-manager, it's great for managing windows partitions especially if you're new to linux.

---

### Post by Verbeck on 2010-11-10
try disk utility from the system > administration menu and select the hard dist from the side bar. if the 'picture' shows three partitions (xgb ext4, Extended xgb, xgb swap) then you probably do not have a dual boot...

---

### Post by Morbius1 on 2010-11-10
Um .... You have no "D partition". In fact you have no windows filesystems present. So unless there's a sdb that fdisk isn't finding something is wrong here.

Please post you fstab:
```
cat /etc/fstab
```It sure does sound like a wubi install in which case your windows partitions will show up under /host and /media in Ubuntu.

---

### Post by JBark1 on 2010-11-10
> **Morbius1 said:**
> Um .... You have no "D partition". In fact you have no windows filesystems present. So unless there's a sdb that fdisk isn't finding something is wrong here.

Please post you fstab:
```
cat /etc/fstab
```It sure does sound like a wubi install in which case your windows partitions will show up under /host and /media in Ubuntu.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I'm looking for the D partition but it didn't consist any Windows Filesystems, it only acted as an important data storage. That is what I'm trying to recover.

---

### Post by Mark Phelps on 2010-11-10
If you actually had a second physical hard drive containing your "D" partition, and you currently have that disconnected, then that data is still intact.

However, according to fdisk, you have only one hard drive.  So, if you really only have one drive, and that originally had "C" and "D" partitions, they are gone now.

It appears that you accidentally used the option to reformat your entire drive.  There are only Linux partitions there, meaning, any Windows stuff is gone now.

---

### Post by Verbeck on 2010-11-10
> **Morbius1 said:**
> It sure does sound like a wubi install in which case your windows partitions will show up under /host and /media in Ubuntu.

but if its a wubi install, wouldn't the file system show as hpfs/ntfs from fdisk (also without swap) :confused:

---

### Post by Morbius1 on 2010-11-10
> **Verbeck said:**
> but if its a wubi install, wouldn't the file system show as hpfs/ntfs from fdisk (also without swap) :confused:
You are quite right that sentence made absolutely no sense :oops:

fdisk only shows / and swap. If the "D" partition exists then it's on a partition that isn't physically connected. I'm afraid Mark Phelps is probably correct in that it's either not connected or it was formatted over to create the Linux install.

---

### Post by JBark1 on 2010-11-10
> **Morbius1 said:**
> You are quite right that sentence made absolutely no sense :oops:
 
fdisk only shows / and swap. If the "D" partition exists then it's on a partition that isn't physically connected. I'm afraid Mark Phelps is probably correct in that it's either not connected or it was formatted over to create the Linux install.
 
Any thoughts on recovering the lost partition D? I have considered using TestDisk but I'm not quite sure.

---

### Post by Mark Phelps on 2010-11-10
Feeling run pretty strong around here as to the "proper" file recovery software to use ...

But in my OWN experience, I have found MS Windows apps doing the best job of recovering/restoring FAT/NTFS partitions and Linux apps doing the best job of recovering/restoring Ext-filesystem partitions.

Either way, you'll need to physically REMOVE the hard drive in question, hook it up to another PC -- and do the file recovery there.

So, what PC you hook it up to will govern whether you use MS Windows utilities or Linux utilities.

---

### Post by bcbc on 2010-11-10
You could boot a live CD, plug in an external drive, install testdisk, but run photorec (it's bundled with testdisk), making sure to direct all recovered files to the external drive.

That will recover raw data files (no names or ordering, but you'll know the type of file) and it will pull off everything that hasn't physically been overwritten. It also ignores partitions and just looks for data on the disk, so it's not dependent on recovering "D:" first. (Yes it'll be hard work to figure out what is what).

After that, you can use testdisk to try and recover the partition.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by JBark1 on 2010-11-11
THANKS EVERYONE FOR THE HELP I RECEIVED!

 I have successfully restored all overwritten Windows partitions without any loss of data – considering that I’ve been using Ubuntu for 2 days on the same HD. TestDisk saved my day.

---

