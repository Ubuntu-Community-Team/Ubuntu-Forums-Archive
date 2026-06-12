---
title: "GParted - Create Partition Table does nothing?"
date: 2009-08-10
forum: General Help
---

### Post by AwaZ on 2009-08-10
Hi, I bought a 64GB usb flash drive today, I plugged in into my computer and nothing happened. So I start up GParted to see if it finds it and it does, but as unallocated space. When I right click it and click New to create a partition table I choose msdos (default) and Create, after 2-3 seconds GParted refreshes with no (visible) changes, and the flash drive still shows as unallocated space..
I need help top format this to FAT32, all help is greatly appreciated. :)

---

### Post by michy99 on 2009-08-10
Can you post a screenshot of what it looks like in gparted?

---

### Post by AwaZ on 2009-08-10
This is what it looks like, if I right click then everything is greyed out except for New (CTRL+N) 

[IMG]http://shahzeb.net/ss.jpg[/IMG]

---

### Post by michy99 on 2009-08-10
New is exactly what you want. Create a new partition and make it whatever filesystem you want.

---

### Post by AwaZ on 2009-08-10
I get no changes when I click New and create a new MSDOS partition table.

---

### Post by orlox on 2009-08-10
Right click on the unallocated space, and that will allow you to add new partitions.

---

### Post by michy99 on 2009-08-10
You want a new PARTITION, not a new partition TABLE.

---

### Post by AwaZ on 2009-08-10
When I rightclick I can only choose New. Which gives me this pop-up 

[IMG]http://shahzeb.net/Screenshot.jpg[/IMG]

---

### Post by michy99 on 2009-08-10
What kind of options do you get under Advanced if you click on the little arrow?

---

### Post by Yvan300 on 2009-08-10
Hmmm, that is quite strange, have you tried other formats as well?

---

### Post by AwaZ on 2009-08-10
Select a new parition table type: msdos (can change to a few other names, aix, amiga, bsd, dvh, gpy, mac, pc98, sun, loop)

Tried them all, some gives the error: Error while creating partition table., most does nothing

---

### Post by michy99 on 2009-08-10
Is there by any chance a switch on the drive that sets it to read-only?

---

### Post by AwaZ on 2009-08-10
Nope

It worked on a windows vista PC earlier, but I tried formatting it to NTFS, which failed. Then it wouldn't work at all on vista, whenever I tried to open it windows said it needed to be formated, but failed doing so.

---

### Post by michy99 on 2009-08-10
Does the drive show up if you enter this in a terminal?```
sudo fdisk -l
```

---

### Post by AwaZ on 2009-08-10
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87486873

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29274   235143373+  83  Linux
/dev/sda2           29275       30401     9052627+   5  Extended
/dev/sda5           29275       30401     9052596   82  Linux swap / Solaris

Disk /dev/sdb: 68.1 GB, 68157440000 bytes
64 heads, 32 sectors/track, 65000 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```
Seems so, but says it doesn't have a valid partition table

---

### Post by michy99 on 2009-08-10
Try this:```
parted /dev/sdb rescue 0 68158
```

---

### Post by AwaZ on 2009-08-10
Error: /dev/sdb: unrecognised disk label

---

### Post by michy99 on 2009-08-10
I'm running out of ideas. Is this a brand new drive? I'm beginning to suspect that it is defective.

---

### Post by AwaZ on 2009-08-10
It is brand new, but like i said earlier it did work on vista earlier, the problem started to happen after I tried (and failed) to use vista to format it to NTFS

---

### Post by michy99 on 2009-08-10
You best bet might be to take it back where you got it and exchange it for another one.

---

### Post by AwaZ on 2009-08-10
Will do, thanks for the help :)

---

### Post by theozzlives on 2009-08-10
Sounds like a bad flash drive, should've come already formatted.

---

### Post by drs305 on 2009-08-10
AwaZ,

Sometimes I just can't get gparted to format a new drive, whether it is a thumb or traditional drive. In these cases, I am able to format it via the command line without problems (I've never had a bad drive, although this is certainly a possibility).

I have my own notes, but the Ubuntu wiki is a good reference. Use the command line to accomplish the steps.
[InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

If you follow all the steps, run "sudo blkid" and "sudo fdisk -l" to see if it shows up. Then start gparted. If it still doesn't show up in gparted, exit gparted, mount the drive manually, then start gparted again.

---

### Post by Ixtao on 2011-05-22
Would also give me the error every time. The action was however performed I discovered after rebooting. Starting gparted from the terminal reveiled the reason of the error;

[INDENT]libparted : 2.3
======================
Partition(s) 1, 3 on /dev/sdb have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes
[/INDENT]So it could be because the partition(s) is/are still mounted. maybe unmount first..

---

