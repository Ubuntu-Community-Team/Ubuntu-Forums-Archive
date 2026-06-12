---
title: "possible to reformat partition to NTFS?"
date: 2010-10-11
forum: General Help
---

### Post by newbie11 on 2010-10-11
Hello,

I am a beginner with Ubuntu. I have Ubuntu running on my PC but I want to install another operating system. The message I am not getting is that I cant install to a partition that is not formatted as NTFS. Do you know how I can reformat my partition to NTFS?

---

### Post by coffeecat on 2010-10-11
> **newbie11 said:**
> The message I am not getting is that I cant install to a partition that is not formatted as NTFS.

That's a triple negative so I can't work out what you're saying. :-k If you mean, can you install Ubuntu to a NTFS partition, the short answer is no. NTFS does not support Linux/Unix permissions which are needed for the OS system files. You can store data and personal files on NTFS but it would be advisable to do so only if you have Windows available to repair any filesystem corruption that might occur. NTFS is a Microsoft filesystem.

> **newbie11 said:**
>  Do you know how I can reformat my partition to NTFS?

Use Gparted from the live CD or install gparted to your HD install. Make sure you have the package ntfsprogs installed as well. It comes in the box with Maverick (10.10), but was not included with some earlier versions. I can't remember whether it comes in Lucid (10.04) so check when and if you  install gparted.

What other OS were you going to install?

---

### Post by newbie11 on 2010-10-11
> **coffeecat said:**
> That's a triple negative so I can't work out what you're saying. :-k



What other OS were you going to install?

Sorry. I should have proofread that. I meant that the message I am getting is that I cant install to a partition that is not formatted as NTFS. I have two PCs running Ubuntu. I am trying to install Windows 7 on one of them as I want to have at least one windows machine.

---

### Post by emoguitarist06 on 2010-10-11
Use gParted as advised above however you cannot adjust the partitions while running Ubuntu so you need to run a live cd/usb

---

### Post by coffeecat on 2010-10-11
> **newbie11 said:**
> Sorry. I should have proofread that. I meant that the message I am getting is that I cant install to a partition that is not formatted as NTFS.

I guess you mean Windows for that double-negative. :p Yes, you can't install Windows to a Linux filesystem. And I'm fairly sure that W7 won't go on a FAT32 filesystem either. 

> **newbie11 said:**
>  I have two PCs running Ubuntu. I am trying to install Windows 7 on one of them as I want to have at least one windows machine.

You may know this already, but if you have Ubuntu already on the machine, installing Windows 7 will take out grub stage 1 so that you won't be able to boot into Ubuntu - temporarily. You will have to repair grub after installing Windows. Useful link here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

