---
title: "GRUB issue for booting between Ubuntu and Ubuntu Studio"
date: 2012-09-03
forum: General Help
---

### Post by djwitowski on 2012-09-03
My goal is to install Ubuntu as the main OS, then strip down Ubuntu Studio for audio recording only. I installed Ubuntu with this structure:
sda1: /boot
sda2: /
sda5: swap
Then I installed Ubuntu Studio, creating a new partition with space from sda2. According to Disk Utility it is sda4, while sda3 is used as a"container for logical partitions."
I don't remember why exactly, but I couldn't get the bootloader to work and eventually re-installed Ubuntu to sda2. I think it had something to do with the out-of-range problem I had, but that I fixed.

My problem now is that I cannot get into Ubuntu Studio. It is installed on the fourth partition. On GRUB for this OS, I have the choice between general and lowlatency (also recovery modes for these two). Choosing general it flashes a few screens, I can get a glimpse of a login prompt in text mode, then it goes to normal Ubuntu. In lowlatency, I get the text console displaying some error, forcing me to reboot. On these options, it does specify that I am choosing the OS on /dev/sdb4. (This is my second hard drive so I assume that is why it calls it sdb, while calling it sda on Disk Utility).
Choosing the first option for normal Ubuntu works fine.

Any help is greatly appreciated.

---

### Post by Bashing-om on 2012-09-03
djwitowski;

 Have you updated grub from the primary operating system ? Such that grub seeks/finds other operating systems and adds them (and config files) to the grub menu ?
```
sudo update-grub
```


[INDENT]regards <==BDQ
[/INDENT]

---

### Post by oldfred on 2012-09-03
Did you attempt to share /boot? You really cannot do that as it will more often than not create conflicts.

You can share swap if you do not hibernate nor have encrypted /home.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by djwitowski on 2012-09-03
Bashing-om: Yes, I have ran update-grub.

Oldfred: I may have tried sharing /boot. I think what I did was, while installing Ubuntu Studio, I reselected the first partition and specified it as /boot. I did that again when installing Ubuntu the second time.

I am sharing swap and do not have an encrypted /home.

I have ran boot-repair twice already. The first time was the recommended repairs, which changed nothing noticeable, then a custom repair in which I re-installed everything.
I will do "Create BootInfo" and post the link it gives me.

Thank you for the replies.

---

### Post by djwitowski on 2012-09-03
[http://paste.ubuntu.com/1184872/](http://paste.ubuntu.com/1184872/)

---

### Post by oldfred on 2012-09-03
Actually I generally prefer not to have a separate /boot. But some very old systems with BIOS limits will only boot from the first 137GB and some very new systems with very large over 100GB / (root) partitions seem to need a separate /boot.

You installed to the same /boot as both fstabs refer to sdb1 although now it is sda1. But Ubuntu uses UUID so it finds correct partition even if drive order changes. By overinstalling you overwrote a grub.cfg as you only have one. Unless kernels were exactly the same version they also may conflict or the new install overwrites the older install. 

Either keep /boot as a folder in / or create two separate /boot, one for each install.
I share swap, and data partitions that have no system files. I have two data partitions, one NTFS to share with XP, now not used much and one Linux format for all new data.

---

### Post by djwitowski on 2012-09-04
Since I hadn't really worked on the systems yet, I wiped the disk and re-installed making sure not to use a separate /boot partition. It does work now. Thanks a lot.

---

### Post by djwitowski on 2012-09-04
.

---

