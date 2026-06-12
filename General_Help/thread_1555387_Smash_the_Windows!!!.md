---
title: "Smash the Windows!!!"
date: 2010-08-18
forum: General Help
---

### Post by chips24 on 2010-08-18
What do i do when i want to format my windows partition?
after i format it will i still have the hard disk space to use on ubuntu?

---

### Post by DarkAmbient on 2010-08-18
> **chips24 said:**
> What do i do when i want to format my windows partition?
after i format it will i still have the hard disk space to use on ubuntu?


My educated guess would be that you format your windows partition into ext3 or ext4 to mount somewhere in Ubuntu. As I guess you allready have ubuntu installed?

---

### Post by Denis Krajnc on 2010-08-18
If you only have one partition and you installed them side by side they you will have space used by Windows, now controlled by Ubuntu.

---

### Post by chips24 on 2010-08-18
yes, they are installed side by side, now how do i rid of my broken windows?

---

### Post by pootan on 2010-08-18
I believe in the system> Administration menu You will find either Disk utility, Gparted or both which will allow you to safely format and/or erase the partition

---

### Post by pzkfw on 2010-08-18
> **chips24 said:**
> yes, they are installed side by side, now how do i rid of my broken windows?

 You're looking for GPARTED (libparted from a terminal). It can be run from inside ubuntu but you can't use it when the drive is being used.  You can boot your Ubuntu CD and do it on live.  It's known as "Disk Partition Manager" or something like that in the gnome menu.  Delete your windows partition (it will be shown as NTFS).  Then make a new ext3 partition, or expand your current ubuntu one to the max size.  Back up life or death data.  Resizing a partition larger shouldn't cause any problems, but it's better to be safe.

---

### Post by chips24 on 2010-08-18
Thankyou for your help.

---

