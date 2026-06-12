---
title: "Booting custom kernel fails."
date: 2004-10-24
forum: General Help
---

### Post by harvie_krumpet on 2004-10-24
I have to compile a custom kernel due to a buggy bios...

I followed the KernelHOWTO on [http://wiki.ubuntulinux.org/KernelHowto](http://wiki.ubuntulinux.org/KernelHowto) - except for the problem that becoming member of the src group wouldn't let me write into /usr/src - no idea why.
Anyway, I sudo'd my way along: loaded the config-file of the 686-kernel, made my changes, compiled the kernel  & installed it with dpkg -i.

It added 

title		Ubuntu, kernel 2.6.8.1.axel-02

root		(hd0,0)
kernel		/vmlinuz-2.6.8.1.axel-02 root=/dev/hda6 ro quiet splash
savedefault
boot

as the first option into my /boot/grub/menu.lst.

Trying to boot now fails with:

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /vmlinuz-2.6.8.1.axel-02 root=/dev/hda6 ro quit splash
   [Linux-bzImage, setup=0x1400, size=0x13d928]
savedefault
boot
Uncompressing Linux... Ok, booting the kernerl.
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

what am I doing wrong?

Thanks!

---

### Post by snowx1000 on 2004-10-30
Same here

---

### Post by butters on 2004-10-30
what filesystem are you using for root?  Did you enable support for this in your kernel?

---

### Post by snowx1000 on 2004-10-30
all filesystems are enabled

also I used make oldconfig, so most of my settings should be there, checked for most.

---

