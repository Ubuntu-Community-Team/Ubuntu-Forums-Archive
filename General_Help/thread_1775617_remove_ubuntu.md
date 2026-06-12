---
title: "remove ubuntu"
date: 2011-06-05
forum: General Help
---

### Post by Neil55 on 2011-06-05
Hi everyone. I want to remove ubuntu and install xp. The xp disc will not boot neither will a windows 98 floppy. I can get to a grub command line on startup but what command can I type to reformat? Thanks for any help

---

### Post by linuxinstalledfromhdd on 2011-06-05
Did you call Microsoft to start a trouble ticket on that?

---

### Post by Hedgehog1 on 2011-06-05
You may have to go into Bios and change the boot order to get the CD to boot before the hard drive.

If it is set to boot from the CD before the hard drive; your CD may be on the fritz.  You can test that by seeing if you can still boot from your Ubuntu LiveCD.

***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-06-05
> **Neil55 said:**
> Hi everyone. I want to remove ubuntu and install xp. The xp disc will not boot neither will a windows 98 floppy. I can get to a grub command line on startup but what command can I type to reformat? Thanks for any help
Hi,if I were you I would not remove ubuntu until you can get the disk to install xp.

---

### Post by Mark Phelps on 2011-06-06
> **Neil55 said:**
> Hi everyone. I want to remove ubuntu and install xp. The xp disc will not boot neither will a windows 98 floppy. I can get to a grub command line on startup but what command can I type to reformat? Thanks for any help

Basically -- you can't.  Why? Because you have to load Ubuntu from the hard drive when you are running it, and you then can not mess with the partition as it is already mounted.

You will need to boot either from a LiveCD or from a USB stick -- and then run the Partition Editor.  But even then, all that will do is erase the partitions from the drive.  It can not be used to install Windows.

You will have to get the CD boot option working.

---

