---
title: "dd not writing images?"
date: 2012-02-16
forum: General Help
---

### Post by rewritw on 2012-02-16
Hi, I'm running ubuntu 10.04.3;

My problem is that I'm trying to make a bootable sd card for the nook color. I followed this guide:   [ http://nookdevs.com/Nookie_Honeycomb:_Burning_a_bootable_SD_card]( http://nookdevs.com/Nookie_Honeycomb:_Burning_a_bootable_SD_card)

When I try to write the image with dd:

```
dd if=/home/soshite/nookhoney04.img of=/dev/mmcblk0p1 bs=1M
```

Of course it takes its time, but once it's done, and I remove it, if I insert it back in again, ubuntu won't read the card anymore no matter what. When I open gparted, it says there are two partitions on the sd card, according to the guide and other sources, after doing that there should be 3 partitions. Not only that, but both partitions are of "unknown formats".\

 I'm not sure what I could be doing wrong, I thought it was the card reader but I have already transferred files and done a file read/write test and it's fine. Maybe my dd is outdated? I also thought I might be getting the wrong device, but then how come it actually re-formats the sd card? I'm at losses. x[

Any ideas? thanks!

---

### Post by winh8r on 2012-02-16
Had a look at the guide and it would seem that you misread this part:


> where <sdcard> is your sdcard (for example /dev/sdc or /dev/mmcblk0,[COLOR="Red"] not[/COLOR] the mount point of the sdcard or an existing partition like sdc1 or [COLOR="Red"]mmcblk0p1[/COLOR]


Best try it again from scratch I would say.

---

### Post by rewritw on 2012-02-16
I thought that too. Until I opened up diskutility. My card says it's mounted at /media/8086-1BEC but the device is /dev/mmcblk0p1 

It used to show up as '/dev/mmcblk0' but now it's been showing up as '/dev/mmcblk0p1'

EDIT

Proof:

```
fdisk -l

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         504     4060160    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 255, 63) logical=(0, 32, 33)
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(503, 158, 30)

```

---

### Post by Seq on 2012-02-16
> **rewritw said:**
> I thought that too. Until I opened up diskutility. My card says it's mounted at /media/8086-1BEC but the device is /dev/mmcblk0p1 

It used to show up as '/dev/mmcblk0' but now it's been showing up as '/dev/mmcblk0p1'

EDIT

Proof:

```
fdisk -l

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         504     4060160    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 255, 63) logical=(0, 32, 33)
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(503, 158, 30)

```

/dev/mmcblk0p1 is the first partition (that's the p1 part). You also appear to have chopped the fdisk output. The top part would have listed the name of your block device (probably mmcblk0p0). I don't have an mmc/sd card handy, but here is my `fdisk -l` on a hard disk, illustrating the same thing:

```
$ sudo fdisk -l

Disk **/dev/sda**: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46b332d5

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1**            2048   195463167    97730560   83  Linux
**/dev/sda2**       195463168   625141759   214839296   83  Linux
```

---

### Post by rewritw on 2012-02-16
Here's the full fdisk:
```
fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031e5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24899   199999488   83  Linux
/dev/sda2           59767       60802     8308737    5  Extended
/dev/sda3   *       24899       59767   280076288   83  Linux
/dev/sda5           59767       60802     8308736   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 4158 MB, 4158652416 bytes
255 heads, 63 sectors/track, 505 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b93c6

    Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         504     4060160    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 255, 63) logical=(0, 32, 33)
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(503, 158, 30)
```

I cut out the rest because I figured it wouldn't matter too much. it says /dev/mmcblk0 but it doesn't look like nothing is mounted. Maybe I am mistaken, but if that is the actual device, shouldn't it unmount it from my desktop if I:
```

umount /dev/mmcblk0

```
because when I do that, it doesn't unmount it, it just says it's not shown in fstab, or something or other. I have to:
```

umount /dev/mmcblk0p1

```

---

### Post by Seq on 2012-02-16
> **rewritw said:**
> Here's the full fdisk:
```
Disk **/dev/mmcblk0**: 4158 MB, 4158652416 bytes
255 heads, 63 sectors/track, 505 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b93c6

    Device Boot      Start         End      Blocks   Id  System
**/dev/mmcblk0p1**   *           1         504     4060160    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1023, 255, 63) logical=(0, 32, 33)
Partition 1 has different physical/logical endings:
     phys=(1023, 255, 63) logical=(503, 158, 30)
```

I cut out the rest because I figured it wouldn't matter too much. it says /dev/mmcblk0 but it doesn't look like nothing is mounted. Maybe I am mistaken, but if that is the actual device, shouldn't it unmount it from my desktop if I:
```

umount /dev/mmcblk0

```
because when I do that, it doesn't unmount it, it just says it's not shown in fstab, or something or other. I have to:
```

umount /dev/mmcblk0p1

```

Nope. There is a difference between devices, partitions, and filesystems. You've got a SD card (mmcblk0). That SD card has one or more partitions (mmcblkp1-mmpblkp*). Each of those partitions can have a filesystem on it (which is mounted at /media/8086-1BEC, according to your earlier post). It is easier if you think of them as containers.

I'm just finishing work for the day, so let me put on my ASCII-art hat. Basically, this is what your device looks like:

```

[-----------mmcblk0-----------]
[----------mmcblk0p1----------]
[----------8086-1BEC----------]
```


The disk image you're flashing probably looks more like this:
```

[-----------mmcblk0-----------]
[--mmcblk0p1--] [--mmcblk0p2--]
[-filesystem1-] [-filesystem2-]
```

So you're right: You need to umount the filesystems before overwriting them. However, you're trying to write a **disk image** which itself contains partitions. It is made to flash to the actual device itself. It may infact even contain some data outside of the partitions (some sort of boot sector, etc). You really do want to flash it to the top-level device.

---

### Post by Seq on 2012-02-16
On a side-note, I'll be doing this this weekend. I just got my Nook Colour back from my wife (though she has now taken my touchpad...).

---

### Post by rewritw on 2012-02-16
I see. I understand. That explains a lot. Thanks for the ascii art, it made me feel extra dumb haha! Thank you sir! Good luck with your nook color roms~!

---

### Post by Seq on 2012-02-16
> **rewritw said:**
> Thanks for the ascii art, it made me feel extra dumb haha! Hah, didn't mean to take it that far, but glad it helped anyway :D

---

