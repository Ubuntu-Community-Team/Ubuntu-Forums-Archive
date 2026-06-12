---
title: "after installing Opensuse cant boot to Ubuntu"
date: 2009-09-06
forum: General Help
---

### Post by bushtangu on 2009-09-06
hi, i has a dualboot pc with XP and ubuntu. yesterday i installed Opensuse, everything worked fine after i discovered that i cant boot anymore to ubuntu. it show me the error boot/vmlinuz-2.6.28-15 missing . all the systems are installed in the same HD. any help please.

---

### Post by bodhi.zazen on 2009-09-06
Did you change your partitions ? Did you install suse over the top of Ubuntu ?

Open gparted and show us your partitions.

To multiboot :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by bushtangu on 2009-09-06
sda 456 Gb ntfs sata HD i use for data 
sdb 40 Gb
sdb1 ntfs XP
sdb3 ext3 Opensuse
sdb2 10.07 Gb
  sbd5 ext3 9.13 Gb Ubuntu
  sdb6 linux-swap 956 mb

---

### Post by bushtangu on 2009-09-06
any help please :S

---

### Post by Atermon on 2009-09-06
I'm afraid I have the same problem. I can't boot into ubuntu at all even though I've installed opensuse on a different hard drive. Also as I try to access my ubuntu hd via opensuse I can't because I have no authorisation. I tried updating the system with my live cd but no success. Can you help please? I'll give away any details if asked, please if you can help reply :(

---

### Post by Atermon on 2009-09-07
fixed it with help from [here]("http://ubuntuforums.org/showthread.php?t=224351")

Turned out error 15 was caused by grub, oh well seems like I got all nerved up for nothing hehe (I would consider  myself a linux newbie ^^):lolflag:

---

