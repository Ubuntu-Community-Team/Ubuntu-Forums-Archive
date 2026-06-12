---
title: "How to trade the order of the boot in the ubuntu 10.10?"
date: 2010-12-14
forum: General Help
---

### Post by TurboThiago on 2010-12-14
I would like to know how to trade the order of the boot in this new version of ubuntu(Ubuntu 10.10). In the others versions i know, but i'm not finding the place in this version. Can anybody help me?
 
Thiago
 
PS: Sorry my bad english

---

### Post by theozzlives on 2010-12-14
> **TurboThiago said:**
> I would like to know how to trade the order of the boot in this new version of ubuntu(Ubuntu 10.10). In the others versions i know, but i'm not finding the place in this version. Can anybody help me?
 
Thiago
 
PS: Sorry my bad english

Order of the boot? A little more info please. Your boot order is set in CMOS.

---

### Post by 73ckn797 on 2010-12-14
BIOS affects the boot order of the hard drive(s) and DVD/CD drives.

Install "startup-manager" from Synaptic to designate which kernel you want to boot into. It does not change the order but only which one you startup on boot. There are other ways to change the order but I have not messed with that. See if this will give you some information: [https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

---

### Post by TurboThiago on 2010-12-14
I have windows 7, ubuntu 10.10 and kurumin 7 in my hard disk. Three operational systems. When i turn on my pc, the grub give me the OS to boot in a list: The first one is kurumin, the second is ubuntu and the third is windows. It's start automaticaly kurumin and i don't use it so much. I would like to trade this order and put ubuntu in the first option. In the previews version of the ubuntu there were a file to be changed in a directory called grub. But i'm not finding it in this version. Anybody know how to do it?

---

### Post by 73ckn797 on 2010-12-14
Grub 2 is different than the old grub and cannot be manipulated the same. The quick fix is using startup-manager until you can figure out the actual re-ordering. Startup Manager will only designate the default kernel you want to startup with.

This link may also provide info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by TurboThiago on 2010-12-14
Thanks, i'll read that article. if i have any other questions about this problem i'll ask here.

---

### Post by oldfred on 2010-12-14
SUM is good for setting an alternative boot with grub2.

But if you want to have Ubuntu first and are not using kurumin much, and it seems like has its boot loader in the MBR, just boot into Ubuntu and reinstall grub from your working Ubuntu. Then Ubuntu will control boot not kurumin.


reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then after rebooting:
sudo update-grub

---

