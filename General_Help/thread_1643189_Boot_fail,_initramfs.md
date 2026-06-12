---
title: "Boot fail, initramfs"
date: 2010-12-11
forum: General Help
---

### Post by jon.mithe on 2010-12-11
Hi,

Having some boot trouble with my parents laptop.  The laptop was 1/2 way through booting up when the power was cut.  When it was powered on it fails to boot and goes to initramfs / a shell.  I'm seeing these sort of errors:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```

Booted up on a live CD, and the HD seems ok. It appears like some info about the boot has been lost / wiped.

So I tried to reinstall / setup grub following this tutorial ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) but I have run into more problems.

Mostly that /boot/grub/... is empty except for a grubenv file which is a comment saying # GRUB Environment Block followed by loads of#########'s.

I'm guessing some core info about the hard drive was wiped, I'm unsure how to fix this.

I can access the hd from the live CD, so I'm thinking I need to find its UUID and stick it somewhere...

Any help would be great thanks.
Jon

---

### Post by jon.mithe on 2010-12-11
Sorted.. sortof...

Yeah followed the directions to reinstall grub. It hasnt quite worked, it looks like I get a random error on boot.  Looks like its trying to find a kernel header or something, but it seems to click past it and load up.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdX
```

Where sdXY is the install partition of ubuntu, i.e. sda1 and sdaX is the hd of the install, i.e. in this case sda

---

