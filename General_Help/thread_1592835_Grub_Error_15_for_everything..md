---
title: "Grub: Error 15 for everything."
date: 2010-10-11
forum: General Help
---

### Post by arkadios on 2010-10-11
I've spent the last 12 straight hours trying to get my computer to boot. It started with the computer just simply not booting, so to get some access to the computer I inserted the Vista Rescue CD and did a fixmbr. That at least got me into my Windows partition but I think that's where I royally screwed up. Over the next eleven hours I've spent my time trying to get into my computer using my LiveCD usb stick and mounting the partition. I've tried everything and nothing works. Now if I boot without my usb stick I simply boot into Grub but even there nothing works. I've tried opening configfiles but all I get are Error 15s saying that the files aren't found. I have no idea what to do at this point. I'm thinking that my best bet is to just .tar up the Ubuntu partition (excluding the grub folders and etc) and wipe/reinstall it, then after that restoring from the tarball. Would this final option even work?

EDIT: [SOLVED] [Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")
[]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by JackNocturne on 2010-10-11
Ok first of all what did you do/change before this problem occurred? 

Grub **error 15** usually means your partitions/disks are ok but it can't find the files needed to boot.

So the solution is to fix the grub i.e Point them to the right files 

Gives more info;
>Use the Live USB to boot into desktop
>Open terminal and type ```
sudo fdisk -l
``` and print the output here

---

### Post by arkadios on 2010-10-11
To be honest, I haven't a clue. I booted my computer when I woke this morning and all it would do was keep booting in a boot loop. I broke out the Windows Restore CD and did the whole fixmbr spiel. After that I kept getting Windows so I broke out the usb stick and eventually got grub installed to the harddrive. Now it just boots straight to grub and nothing else.
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a645180

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1162     9325568   27  Unknown
/dev/sda2   *        1162        9414    66291363    7  HPFS/NTFS
/dev/sda3            9415       12589    25503187+   7  HPFS/NTFS
/dev/sda4           12590       19458    55168001    5  Extended
/dev/sda5           12590       13865    10245120   82  Linux swap / Solaris
/dev/sda6           13865       19458    44921856   83  Linux

Disk /dev/sdb: 4005 MB, 4005560320 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         487     3911638+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(486, 249, 63)
```

---

### Post by JackNocturne on 2010-10-11
By the way do you know which GRUB **version** you are using? Cos' it will make this easier.
There is grub-legacy( ~0.98 aka Old) and Grub2(~1.98 aka new)

I assume you wanted Grub to be installed in **sda6** which is your linux partition?

---

### Post by arkadios on 2010-10-11
I did a clean install about a year ago so I'm pretty sure it's Grub2 and yeah, it's sda6.

EDIT: I fixed the whole Grub deal, used: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by JackNocturne on 2010-10-11
Sorry for late reply, i was about to write the solution but was caught up with work. Well its good to hear Grub works now. Cheers mate.

---

