---
title: "How do I tell what hard drive sda is in GRUB? (e.g.: hd0, hd1)"
date: 2009-08-17
forum: General Help
---

### Post by Bradj47 on 2009-08-17
I'm trying to link the GRUB menu that comes up before Solaris when I boot it to the one that comes up before Ubuntu when I boot it. I already successfully made an option on the Ubuntu GRUB menu that links to the Solaris one (hd1,0), but I can't get the Solaris GRUB to bring up the Ubuntu GRUB. I've tried (hd0,0),(hd0,1), and (hd0,2). None of them worked. I also tried checking the Ubuntu boot commands in grub but it didn't mention the name of any disks, it just had this:
```

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c532ecb-2908-49be-95d5-17de21ce2288 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2c532ecb-2908-49be-95d5-17de21ce2288
kernel		/boot/memtest86+.bin
quiet

title		Solaris 10 5/09
root (hd1,0)
makeactive
chainloader +1

```
Is there a command I can run in the Ubuntu Terminal to tell the name of the disk I'm running it on?

---

### Post by Bradj47 on 2009-08-17
Bump?

---

### Post by supremedalek on 2009-08-17
AFAIK, the root=something defines which partition in which disk to call, well, root. Two ways it can be defined is using /dev/partition (which could be off LVM), as in (stolen from a debian box I know)

```
title           Debian GNU/Linux, kernel 2.6.26-1-686
root            (hd0,0)
kernel          /vmlinuz-2.6.26-1-686 root=/dev/hda3 ro
initrd          /initrd.img-2.6.26-1-686

```

or using the uuid associated with that drive. Yours seem to be using the latter but does not seem to specify the partition besides saying "hey, this is the uuid for the drive I want to boot from!" How is your layout? In my ubuntu 9.04 desktop at work, the menu entry looks like

```
title           Ubuntu 9.04, kernel 2.6.28-14-generic
uuid            135049bf-5ec4-41b5-b067-20889b018ee1
kernel          /vmlinuz-2.6.28-14-generic root=/dev/mapper/raub-root ro quiet splash
initrd          /initrd.img-2.6.28-14-generic
quiet

```

I would even say your

---

### Post by oldfred on 2009-08-17
You need to install one more grub.

How to multiboot:
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

comment in above.
By far, the easiest way to do this is to install grub BOTH to the MBR and your root (or /boot) partition with each install.

---

### Post by asmoore82 on 2009-08-17
to get the Solaris GRUB to boot Ubuntu,
you probably need to chainload the whole(MBR) Ubuntu disk and
not single out any particular partition;
so it would be **(hd0)**

---

### Post by bryanl on 2009-08-17
See [Ubuntu Guide boot from usb](https://help.ubuntu.com/community/BootFromUSB)

The idea is to put a file with a unique name on the root of your bootable system. Then reboot and get to Grub's command line. Tell it to find the file and it will return the drive and partition identifier where it finds it. You can then set root, chainloader and boot.

---

