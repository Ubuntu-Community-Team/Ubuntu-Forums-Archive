---
title: "Ubuntu no longer boots (no longer have a partition table?)"
date: 2006-02-20
forum: General Help
---

### Post by ender42 on 2006-02-20
So I had a working instance of Ubuntu.  I (regretfully) shutdown, installed some new memory, and thought about installing a DVD burner (didn't actually plug a power supply into it).

Reboot.

Get grub, can do a memory check (I believe that's working, as I completely replaced my memory and I'm running off a warty live CD right now...), and it's stuck on a memtest.

I was told that I need to go into /boot and check for the grub menu etc.

So I mounted up my primary drive:  
mount -t ext2 /dev/hda1 /mnt/hda1

Got directories and stuff...

Was attempting to figure out what things were where and did this:
[edit]fdisk -l /dev/hda


/boot/grub/menu.lst appears to be working:
default         0
timeout         3
hiddenmenu
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot

Suggestions?

---

