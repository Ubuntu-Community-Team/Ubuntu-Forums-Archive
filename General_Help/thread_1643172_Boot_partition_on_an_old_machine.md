---
title: "Boot partition on an old machine"
date: 2010-12-11
forum: General Help
---

### Post by tweezak on 2010-12-11
I've done a lot of searching on this but haven't found a concise solution to my issue. Maybe there isn't one.

A little history first:

I installed using WUBI. I had already shrunk my Windows partition (using Windows disk management) and created a partition for Ubuntu and for swap space. I thought WUBI would give me a chance to choose the partition for installing but I was mistaken (I should mention I'm a bit of a n00b).

Anyway, after running Ubuntu for a while from the WUBI install I did an Ubuntu update and GRUB got corrupted. I had to use my Windows XP disk to repair my MBR. No big deal. But at this point I decided it was time to do a REAL Ubuntu install on the partition I'd created for it.

Now we get to the part where I have issues. I think I need to create a boot partition for GRUB somewhere in the very early part of the drive. This is because my machine is old and has the BIOS issue where the boot sector must be in the first 1024 cylinders of the drive.

Of course, Microsoft has taken that space and I don't know how to insert a new partition without hosing my Windows install. I also have a large data partition that I don't want to lose. It's SDA5 in the list below.

I think there's also an issue with the number of partitions I have. I think I can only add logical partitions.

Any guidance would be greatly appreciated. Thank you in advance.

[FONT=Courier New]Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06d506d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       12617    39905460   83  Linux
/dev/sda3           12618       12748     1052257+  82  Linux swap / Solaris
/dev/sda4           12749       36480   190627259+   f  W95 Ext'd (LBA)
/dev/sda5           12749       36480   190627258+   7  HPFS/NTFS[/FONT]

---

### Post by MrFaler on 2010-12-11
I have done this a couple of times, I used Acronis Disk Director (a Windows program) it is a paid program, but there is a trial available. It allows for many more advanced actions that Windows disk management doesn't support.

You will be able to move your partitions and Windows will still run.

BTW Wubi installs in a virtual HD on your Windows partition. There is no need to partition your drive when using it.

---

### Post by oldfred on 2010-12-11
As long as your sda2, the linux partition is totally within the 137GB limit (you have to have a real old system to have smaller than that) you should be ok.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by tweezak on 2010-12-22
> **oldfred said:**
> As long as your sda2, the linux partition is totally within the 137GB limit (you have to have a real old system to have smaller than that) you should be ok.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks for pointing me to that. It worked great...I think.

Problem is I can't tell if I'm in the moved install on the new partition or still in the old WUBI install in the Windows partition. How do I tell the difference? The boot process appears the same.

---

### Post by oldfred on 2010-12-22
If you are booting windows first, you get the windows & Ubuntu choice, then you get the grub menu.

If you are booting with grub you just get the grub menu.

To see if it installed correctly, sometimes grub is not installed correctly:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by tweezak on 2010-12-23
I was able to use the following command to tell where root was located. 

```
mount | grep ' / '
```It shows it is on the new partition so I'm off and running. Thanks to everyone for your help!

---

