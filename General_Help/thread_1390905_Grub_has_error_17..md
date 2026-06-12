---
title: "Grub has error 17."
date: 2010-01-26
forum: General Help
---

### Post by ajmburgos09 on 2010-01-26
Even though I didn't try to update windows (dual-boot), something has gone wrong and grub said "Error 17." Before that, the dual-boot system worked perfectly. Is there any reason why it would do that? Right now I'm using a live ubuntu cd. I hope this data would help you. Thanks!

root@ubuntu:/# sudo fdisk -l

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        8568    67282944    7  HPFS/NTFS
/dev/sda3            8569        9729     9325732+   5  Extended
/dev/sda5            8569        9673     8875881   83  Linux
/dev/sda6            9674        9729      449788+  82  Linux swap / Solaris

```

---

### Post by SuperSonic4 on 2010-01-26
Which version of ubuntu/grub are you using?

Have you tried changing the boot order in BIOS?

---

### Post by ajmburgos09 on 2010-01-26
I'm using ubuntu 9.04, bu I don't know what version of grub I am using (I'm a noob in ubuntu).

---

### Post by SuperSonic4 on 2010-01-26
That's no problem, 9.04 uses legacy grub so can you post the output of ```
cat /boot/grub/menu.lst
```

---

### Post by ajmburgos09 on 2010-01-26
```
root@ubuntu:/# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

---

### Post by oldfred on 2010-01-26
Because you are running from the liveCD your location of menu.lst is down a level or two in a /mnt...

[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)
Herman recommends a filesystem check - see link for other recommendations and how to run from a liveCD:
 A file system check should fix it in almost all cases. This is a good thing to try first because a file system check is always helpful even if the file system is okay and it may solve the GRUB Error 17 problem right away if the file system did need repairing.

---

### Post by ajmburgos09 on 2010-01-27
About the boot stuff, the menu of OSes doesn't even appear, and it immediately says error 17.

I tried to experiment with Super Grub to see what I can do. At first, I tried fixing grub, but it always says error 15, no file found. Because of this I activated my Vista partition. It worked, and now I tried to access the files in Ubuntu using ext2ifs, but whenever I try to open the drive where ubuntu is, it says that the disk isn't formatted.

Also tried fsck-ing /dev/sda5 (the ubuntu partition), but when I try to mount it, it says 

```
mount /dev/sda5
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

```

---

### Post by ajmburgos09 on 2010-01-27
I tried using Super Grub after fsck-ing /dev/sda5, and tried to boot ubuntu in it, and it worked! After that, I used update-grub to have that good old grub menu.

Thanks guys! I thought I had to lose my files and reinstall Ubuntu again.

---

