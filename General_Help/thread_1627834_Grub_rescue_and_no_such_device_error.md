---
title: "Grub rescue and no such device error"
date: 2010-11-21
forum: General Help
---

### Post by AliAlghamdi on 2010-11-21
Hello guys, i just don't have an idea what did i do wrong!

I installed Ubuntu with Wubi and it worked ok for hours until i updated it, then it asked for reboot. So I did.

when i rebooted the laptop i got this problem

error: no such device: e5589151-8c9a-42c0-b2a1-8258647c8a9e
grub rescue >

the weird thing that i can't boot window and ubuntu. 

i don't have Win cd or recovery cd. I downloaded LiveCD and burned it but it's not working and says a problem with some dir.

I'M REALLY Afraid. i don't know what to do. I tried most ways nothing worked.

Help please, thanks in advance

---

### Post by northern lights on 2010-11-21
Please post the exact error message the LiveCD responds with.
Most likely it's a bad burn. Have you checked the md5 hash?

Are you running the danger of losing non-backed up data?
If so, boot from any LiveCD or pen drive. Ubuntu LiveCD or [Knoppix]("http://www.knoppix.net/") are advisable choices. Back up data.

From a working Live distribution, post the output of```
fdisk -l
```(Lower case L, run as root)

---

### Post by AliAlghamdi on 2010-11-21
I checked MD5 hash it's ok!  and i'm not afraid of losing data, but i prefer a peaceful option.

the liveCD problem is 

(initframs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

this is the exact problem. now i'm downloading Knoppix. and let's see

---

### Post by AliAlghamdi on 2010-11-21
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2167    17405403+   c  W95 FAT32 (LBA)
/dev/sda2            2168       17367   122094000    7  HPFS/NTFS
/dev/sda3           17368       60801   348883605    f  W95 Ext'd (LBA)
/dev/sda5           17368       58162   327685806    7  HPFS/NTFS
/dev/sda6           58163       60801    21197736    7  HPFS/NTFS


```

i got this

---

### Post by bcbc on 2010-11-22
You need to reinstall the windows bootloader. When you run a grub-update it prompts you to choose a device (/dev/sda ring a bell) and then if you select it, it installs grub to the drive MBR. Which is great on a normal Ubuntu install, but doesn't work for wubi.

So - since you don't have a wubi install, you can use lilo. I'm not sure how you install it from knoppix, but from an ubuntu live CD you would run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by AliAlghamdi on 2010-11-22
> **bcbc said:**
> You need to reinstall the windows bootloader. When you run a grub-update it prompts you to choose a device (/dev/sda ring a bell) and then if you select it, it installs grub to the drive MBR. Which is great on a normal Ubuntu install, but doesn't work for wubi.

So - since you don't have a wubi install, you can use lilo. I'm not sure how you install it from knoppix, but from an ubuntu live CD you would run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Thank you. it worked

---

### Post by nthali on 2010-11-22
Hello folks,
Yet another "no such device" issue, but this thread gives me hope.
did pretty much the same thing - chose the main /dev/sda as the boot loader device, and now neither windows nor ubuntu can boot up.
i have the 10.10 CD. question i have is: where exactly do i run those sudo commands mentioned above to reinstall the lilo?
thanks,
nilesh

---

### Post by nthali on 2010-11-22
Never mind. with the patience of a gnat, i decided to do the "try ubuntu", brought up a terminal, and ran the two commands you provided, and things are back to normal now.

i must say that after several (possibly half-baked) failed attempts to install ubuntu alongside my WinXP (encrypted with PointSec), and also on an external hard drive, i'm not getting anywhere.

what documentation should i look at to get a good understanding of GRUB2 and all this other stuff that allows BCBC to provide these sudo commands that get things working again?

Thanks,
Nilesh

---

### Post by bcbc on 2010-11-22
There's no decent documentation on grub2 that focuses on Wubi. You can go to launch pad and read the bug reports that have been around since April this year when 10.04 came out - since then I have advised many people how to get their computers booting again.

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417)

The original 10.04 bug - that impacted all dual boot users (not just wubi).[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

The latest update is from this [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581760](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/581760)

---

