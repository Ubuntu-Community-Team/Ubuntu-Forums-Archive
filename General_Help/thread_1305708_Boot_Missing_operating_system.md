---
title: "Boot: Missing operating system"
date: 2009-10-30
forum: General Help
---

### Post by VeskoJl on 2009-10-30
I have single boot Jaunty and from nowhere today I can't boot my system. POST gives me "Missing operating system"???
How to troubleshoot this?

---

### Post by blazemore on 2009-10-30
Are you sure you haven't left a flash drive plugged in?



You're welcome, no need to reply :P

---

### Post by unmole on 2009-10-30
It might be corrupt HD. Try booting into a Live CD and see if you can access your HD.

---

### Post by JBAlaska on 2009-10-30
1-Floppy disk in drive (I know what's a floppy drive)
2-Music CD in CD-Rom
3-Harddrive detect set to none in the BIOS
4-IDE or SATA turned off in BIOS

If it's not one of those..See post above

---

### Post by VeskoJl on 2009-10-30
No flash , no disk in floppy!
But could be a problem with the SATA drive!
Can GRUB be the problem ?


unmole, do you mean to try mounting it?

---

### Post by JBAlaska on 2009-10-30
Since POST comes before grub, prolly not. Enter your BIOS setup and see if it's even detecting your SATA drive. If not take it out and put in the freezer for an hour, then put it back in and see if it boots...if so, quickly backup all your mission critical data, cause the drive is failing...BTW this really works alot of the time.

---

### Post by VeskoJl on 2009-10-30
BIOS detects the drive. Now will try it with hiren's boot!

---

### Post by blazemore on 2009-10-30
Don't use Hiren's! Just use your Ubuntu disk.

---

### Post by VeskoJl on 2009-10-30
From Live CD i can access the drive. Mounting and reading!
Some fscheck tool ?
Could this be a MBR problem , since it's in POST stage?

---

### Post by JBAlaska on 2009-10-30
You can look at the drive with gparted and check your boot flag and partitions and run FSCK (This needs to be done on an un-mounted drive) So the Live CD is a good choice.

---

### Post by VeskoJl on 2009-10-30
Done. Only strange thing i see is that my root is extended not primary, but still have /boot as primary.

---

### Post by JBAlaska on 2009-10-30
Well Linux will run on a extended partition. Try posting the output of ```
sudo fdisk -l
```

---

### Post by VeskoJl on 2009-10-30
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25       10011    80220577+   5  Extended
/dev/sda5              25        3063    24410736   83  Linux
/dev/sda6            3064        3428     2931831   82  Linux swap / Solaris
/dev/sda7            3429       10011    52877916   83  Linux

---

### Post by JBAlaska on 2009-10-30
There are several ways to repair grub at this point both GUI and CLI, but imho the easiest and most successful way is to use [Super Grub Disk](http://www.supergrubdisk.org/) I've had good luck with this tool. Also here's a [Link](https://help.ubuntu.com/community/GrubHowto) to the Grub Wiki.

---

### Post by VeskoJl on 2009-10-30
Super Grub Disk did the job! 
So this was a GRUB problem, like every time.

Thanks, JBAlaska!
Thanks to all for the time and hints.

---

