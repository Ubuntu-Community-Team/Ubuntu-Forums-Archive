---
title: "How do you remove GRUB and restore MBR?"
date: 2010-01-11
forum: General Help
---

### Post by the lemming on 2010-01-11
Any advice would be appreciated.

Cheers

---

### Post by Leppie on 2010-01-11
there's several ways.
use the windows recovery console (requires the installation disk).
use one of the many images with boot and partition tools.
use the ubuntu livecd and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  ##replace /dev/sda with the disk you want to reset the mbr of
```

---

### Post by the lemming on 2010-01-12
> **Leppie said:**
> there's several ways.
use the windows recovery console (requires the installation disk).
use one of the many images with boot and partition tools.
use the ubuntu livecd and issue these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  ##replace /dev/sda with the disk you want to reset the mbr of
```



Thank you for the helpful advice.  Unnfortunately I am hopeless with the command line and if I could press on you for a little mor information, could you please help me with the last part of the text you gave me?

##replace /dev/sda with the disk you want to reset the mbr of

I ma sorry but I do not understand this bit.  My laptop has one disk which has been partitioned to allow a dual boot of Vista and Ubuntu.  As far as I am aware Vista is on the first partition.

Cheers

---

### Post by Techsnap on 2010-01-12
The best method is using the Windows CD have you have access to it, the lilo method will work but it's probably easy for you to try the Windows discs first. 

Do you have Vista/7 or XP/2000?

> ##replace /dev/sda with the disk you want to reset the mbr of

Try running

```
sudo fdisk -l
```

It will list all your hard drives, you'll be able to tell what your primary hard drive is as it usually is sda.

---

### Post by Leppie on 2010-01-12
> **the lemming said:**
> Thank you for the helpful advice.  Unnfortunately I am hopeless with the command line and if I could press on you for a little mor information, could you please help me with the last part of the text you gave me?

##replace /dev/sda with the disk you want to reset the mbr of

I ma sorry but I do not understand this bit.  My laptop has one disk which has been partitioned to allow a dual boot of Vista and Ubuntu.  As far as I am aware Vista is on the first partition.

Cheers
sometimes people have several disks in their system. if you have only one, then just ignore the part after the hashes. so just use:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
that should do it (don't worry if there's some warnings when installing lilo, that's normal).

---

