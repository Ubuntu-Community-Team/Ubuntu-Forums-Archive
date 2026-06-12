---
title: "Upgrading Dualboot"
date: 2010-05-19
forum: General Help
---

### Post by bizhat on 2010-05-19
I have windows + ubuntu 9.04 dual boot.

I have downloaded install CD for ubuntu 10.04.

I have backed up files in ubuntu installation. I am planing to delete existing ubuntu partition from windows and reinstall ubuntu as normal. 

Since current boot loader is grub, and it is deleted, will it create any problem in detecting windows installation ?

---

### Post by wilee-nilee on 2010-05-19
> **bizhat said:**
> I have windows + ubuntu 9.04 dual boot.

I have downloaded install CD for ubuntu 10.04.

I have backed up files in ubuntu installation. I am planing to delete existing ubuntu partition from windows and reinstall ubuntu as normal. 

Since current boot loader is grub, and it is deleted, will it create any problem in detecting windows installation ?

Just to make sure you have windows and ubuntu on separate partitions and grub is the bootloader, this is not a wubi install correct.

Yes you can delete Jaunty and install Lucid in it's place and grub2 should have no problems finding windows. 

Now you want to make sure that you only install grub in the hard drive not a partition. Which means if you have a single HD this would be sda. You might post from the terminal 1st, 

sudo fdisk -l 

Just to confirm the HD setup. l= a small case L, and here is a grub2 wiki for future reference.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Lucid comes with grub2, make sure lucid runs okay with a live cd first.

---

