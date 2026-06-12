---
title: "System refuses to boot at the first attempt"
date: 2011-04-29
forum: General Help
---

### Post by printfw on 2011-04-29
Hi, everyone. After the upgrade to natty my system started to refuse booting at the first attempt. More details: on the grub menu i'm trying to start ubuntu and this causes errors:
```
error: file not found
error: you need to load the kernel first
push any key to proceed
```
Then grub menu shows up again. After some attempts to start the error messages don't appear and system boots up normally. That happens every time.
*fdisk -l* output:
```
/dev/sda1   *           1       10199    81922016+   7  HPFS/NTFS
/dev/sda2           10199       30402   162276352    f  W95 extended (LBA)
/dev/sda5           10200       10759     4498168+  82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris
/dev/sda6           15623       30402   118714368   83  Linux
/dev/sda7           10760       14771    32225280   83  Linux
/dev/sda8           14772       15622     6834176   83  Linux
```
The */* directory (*/dev/sda7*) is formatted as *reiserfs*.
Any idea how to resolve this issue?

---

