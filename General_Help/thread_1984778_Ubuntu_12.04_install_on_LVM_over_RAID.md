---
title: "Ubuntu 12.04 install on LVM over RAID"
date: 2012-05-22
forum: General Help
---

### Post by zeukiki on 2012-05-22
Hello,
 I would install the latest version of Ubuntu on my computer.
 For 2 years I have the same hardware configuration on the old LTS version (10.04) and I wanted to change to a newer version of Ubuntu.
 But during those two years I could see that when I put the updated grub package, then I had trouble getting started my Ubuntu. Indeed, it could not properly install grub in the MBR of any hard drives and which constitute my RAID.
 So I decided to install version 12.04 of Ubuntu and I came across the same error, namely 
```
/usr/sbin/grub-setup : attention : Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea.. /usr/sbin/grub-setup : erreur : l'installation est impossible, mais reste nécessaire quand le périphérique racine est une grappe RAID ou un volume LVM.
```
 I'm in a situation where I know how to re-install Ubuntu 10.04 , but I can not do the same with version 12.04.
 My hardware configuration is as follows:
 - Class processor amd64
 - 7 Drives in RAID5
 - LVM covering the whole space of RAID5, divided into three partitions, a root, a home and a swap.

 For installation, I proceed as follows:
 - Boot the liveCD
 - Installation of package mdadm and mdadm-As
 - Installation of package lvm2, then sudo partprobe
 So before I end up with my installation disks as they should be, then:
 - I run the installation, by selecting the partition manually.
 - I select my "/dev/mapper/newlvm-home" I do not format and which I attribute the mount point "/home"
 - I select my "/dev/mapper/newlvm-root" I format it and which I attribute the mount point "/"
 - I select my "/dev/mapper/newlvm-swap" which I attribute exchange space.

 The installation continues, and after I get this error who said that grub cannot install grub on MBR.

 If someone could help me to find a solution or explain why I can not do that?

Thanx.

---

### Post by zeukiki on 2012-05-23
Hi,
I have try to install Ubuntu with desktop version 64bits, and alternate 64bits, and i get the same error, no idea ?

Thanx

---

### Post by zeukiki on 2012-05-24
Hi,
Here is my boot-repair report, it may help ==> [here]("http://paste.ubuntu.com/1003855/")

Thanx

---

### Post by YannBuntu on 2012-05-24
> **zeukiki said:**
> Here is my boot-repair report, it may help ==> [here]("http://paste.ubuntu.com/1003855/")

Hello
You may need a separate /boot partition outside your RAID/LVM.

(avez-vous ouvert une discussion sur le forum ubuntu-fr?)

---

### Post by zeukiki on 2012-05-24
> **YannBuntu said:**
> Hello
You may need a separate /boot partition outside your RAID/LVM.

(avez-vous ouvert une discussion sur le forum ubuntu-fr?)

Hi,
Yes this is the same post as ==> [http://forum.ubuntu-fr.org/viewtopic.php?id=931301]("http://forum.ubuntu-fr.org/viewtopic.php?id=931301")

Can you explain your point of view in my topic on ubuntu-fr.org ?

---

