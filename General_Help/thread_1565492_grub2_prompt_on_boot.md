---
title: "grub2 prompt on boot"
date: 2010-09-01
forum: General Help
---

### Post by cheshirekow on 2010-09-01
(here's the full story, skip to the next paragraph for just the problem description): I have an old dell laptop that has been retired from being my main work machine. As I've migrated to Ubuntu on every thing else, I figured I would drop the last tie to windows and install it on this machine for screwing around at home. However, I seem to be having a lot of trouble getting 10.04 to work correctly. I first installed it two or three times because I forgot that the nvidia cards need "nomodeset" or the laptop will give just a blank screen. So I added "nomodeset" to the advanced options and reinstalled again. Following this, thing seemed to work fine. I booted into ubuntu, checked that things were working, installed a few programs, then shut down. The next day I booted again, and then upgraded everything ("sudo apt-get update; sudo apt-get upgrade"). After that I cannot seem to boot up normally anymore. 

Now, whenever I try to boot, immediately following the BIOS boot screen, I get the grub 2 prompt. At first I used the following to get ubuntu to boot:

```

grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-...
grub> initrd /boot/intird-...
grub> boot

```

That worked once, but then I shutdown, and the next day it did not work again. I got a message saying "gave up waiting for root device" ... "dropping to a shell". Now I've changed to the following:

```

grub> set root=(hd0,1)
grub> probe (hd0,1) -u
[prints out UUID]
grub> linux /boot/vmlinuz-... root=UUID=[thing from above] rootdelay=90
grub> initrd /boot/initrd-...
grub> boot

```

This seems to have worked several times. I edited /etc/default/grub to add "rootdelay=90" to the configuration, and then ran update-grub. However, whenever I boot the machine still goes directly to a grub 2 console *immediately* after the BIOS splash screen.

Any ideas on what the problem could be, how I can diagnose the issue, or what to do to solve it?

P.S. I did a fresh install using the whole hard disk, letting ubuntu set the partitions. It chose to create one primary partition for the file system, and one extended partition (I think that's what it's called, or is it a secondary partition on an extended partition) for swap: 

```

sda1        ext4    /
sda2
  sda5      swap    swap

```

I thought that was a little weird because I think when I installed it on my other machines it always made the swap partition a primary partition. But I didn't pay close attention so maybe not. More importantly though, this is not a dual boot with windows and this is not a WUBI install so the thousand other threads on the forums don't seem to apply.

---

