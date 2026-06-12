---
title: "Unable to allocate swap"
date: 2009-07-14
forum: General Help
---

### Post by maddyuk on 2009-07-14
Hello Ubuntu geeks,

Have installed Ubuntu 9.* as a virtual machine. Below is the output for *fdisk -l*

/dev/sda1   *           1         367     2947896   83  Linux
/dev/sda2             368         391      192780    5  Extended
/dev/sda5             368         391      192748+  82  Linux swap / Solaris

Have modified */etc/fstab* to use */dev/sda5* in place of UUID. However after rebooting, the swap is not allocated by default. if I do *swapon -a* I get the following error

[I]swapon: cannot stat /dev/disk/by-uuid/\x2fdev\x2fsda5: No such file or directory
[/I]
If I do *swapon /dev/sda5* , swap is being allocated but needs to be run after every reboot.

Any idea what could be wrong?

---

### Post by geirha on 2009-07-14
It looks like you set the device to ```
UUID=/dev/sda5 
``` in your /etc/fstab. It should be just ```
/dev/sda5 
``` if you want to name it by device node. However I do recommend you use the UUID. To see the actual UUID of /dev/sda5, run ```
sudo blkid /dev/sda5
```

The most common case where your swap partition's UUID change is when you do some partitioning that affect the swap partition, so after doing some partitioning, it's a good idea to check that the UUID of your swap matches the UUID in /etc/fstab.

---

### Post by maddyuk on 2009-07-14
Absolute spot on!!!

working now.

cheers

---

