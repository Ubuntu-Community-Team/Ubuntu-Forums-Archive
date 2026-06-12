---
title: "Installing GRUB2 from Live CD to slaved drive"
date: 2010-05-12
forum: General Help
---

### Post by 98cwitr on 2010-05-12
Can someone tell me how to do this? I just formatted a slaved drive for EXT4 and now I'd like to write grub over the MBR. Cannot really find much on Google. tried:

grub-install /dev/sda1 and of course didn't work....

---

### Post by 98cwitr on 2010-05-12
anybody?

---

### Post by linuxman94 on 2010-05-12
GRUB is installed to the MBR of the drive so to install grub, the command would be:

```
sudo grub-install /dev/sda
```

---

### Post by 98cwitr on 2010-05-12
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by 98cwitr on 2010-05-13
bump

---

### Post by Sef on 2010-05-13
1) Please wait 24 hours with no response to your thread before bumping it.   Thank you.

2) Read Ubuntu Doc's [GRUB 2]("https://help.ubuntu.com/community/Grub2") and the Ubuntu Wiki's [GRUB 2]("https://wiki.ubuntu.com/Grub2").

---

