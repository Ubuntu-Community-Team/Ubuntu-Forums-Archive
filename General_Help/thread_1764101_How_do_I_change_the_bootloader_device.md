---
title: "How do I change the bootloader device?"
date: 2011-05-21
forum: General Help
---

### Post by doko1 on 2011-05-21
Hi.

I have a desktop pc with two hard disks. On one is Windows XP (which i never  use), on the other Ubuntu 11.04. 

My problem is, that the hard disk with Windows XP on it is broken. I can't start Windows XP anymore but I can mount this hard disk in Ubuntu. However, it has troubles to read it or copy files from it.  
If I disconnect this broken hard drive,  booting doesn't work, even though I tagged the Ubuntu hard drive as "bootable" with GParted. 

I'm afraid, that the bootloader is on that broken device. I've been searching in internet for a long time, how to change the device (move it to the healthy ubuntu hard drive), but didn't find a solution. 

Does anybody know a solution to this problem?

---

### Post by ambdeep on 2011-05-21
try:
```
sudo grub-install /dev/sd*
```
where * is the name of the hard drive you want to select.

to check for available hdds:
```
sudo fdisk -l
```

---

### Post by Quackers on 2011-05-21
Boot into Ubuntu and confirm which hard drive designation is used by Ubuntu (eg /dev/sdb) then open up a terminal and run
```
sudo grub-install /dev/sdX
```
The /dev/sdX needs to be changed to the drive designation of the drive used by Ubuntu (eg /dev/sdb)

EDIT Of course you will then need to set your bios so the Ubuntu hard drive boots before the other one.

---

### Post by doko1 on 2011-05-21
Great! It worked!

Thank you so much! :)

---

### Post by Quackers on 2011-05-21
Glad to hear it :-)
You're welcome!

---

