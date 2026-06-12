---
title: "Won't boot to X, booting into BusyBox"
date: 2010-01-21
forum: General Help
---

### Post by gnulnx on 2010-01-21
Hey everyone.

My system was hanging so I gave it a reboot.  After coming back up, the system is booting into BusyBox.  I have tried booting into the Ubuntu LiveCD and then mounting my / in /mnt and my /boot in /mnt/boot and then doing a grub-install.  This doesn't seem to have fixed my issue.  I have also tried booting to the second drive in my raid 1 array.

Here is what I see on my screen:
```

mount: mounting /dev/disk/by-uuid/a4aad87c-c45b-4480-84fa-e0290f5a7853 on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Targeet filesystem doesn't have /sbin/init.
No init found.   Try passing init= bootarg

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```I am running Ubuntu 9.10 64bit w/ 2 disks in raid 1.  My partition table is like:
```
/dev/sda1 /boot   raid autodetect   ext4
/dev/sda2    raid autodetect    swap
/dev/sda3 /root    raid autodetect    ext4
/dev/sda4 extendd
/dev/sda5 /home/user/.VirtualBox    raid autodetect    xfs
/dev/sda6 /home    raid autodetect ext4
```If you need any more info, please ask.  Thanks!

---

### Post by gnulnx on 2010-01-21
I have since tried repairing grub a different way: booting to the livecd, mounting /dev/sda1 (my boot partition) to /boot, and then doing gnome-install /dev/sda, the output of which is
```
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
```
And I have still the same behavior: booting into busybox.  Any other ideas?

---

### Post by gnulnx on 2010-01-22
Bump.  If I can provide any more info, please let me know.

---

### Post by gnulnx on 2010-01-25
halp

---

### Post by sithlordkyle on 2010-01-26
i had this problem once with 9.04 and, while this may not sound great, i only solved it by reinstalling.  hopefully someone with better knowledge than i comes along soon!

---

### Post by gnulnx on 2010-01-27
I did create a separate partition for /home, so reinstalling should be easy.  Easy, but hopefully unnecessary!

---

### Post by kd5dbl on 2010-02-26
While I know this doesn't help one bit but...

I got the exact same thing this morning... Box had been up and running for about 2 weeks and then just locked up.  Tried every way I knew to get in to it and finally had to power cycle it.

I'm getting the exact same... did you ever come up with a solution?  Or did you just rebuild it?

---

### Post by gnulnx on 2010-02-26
Unfortunately, I never figured it out and just did a reinstall.
:(

---

