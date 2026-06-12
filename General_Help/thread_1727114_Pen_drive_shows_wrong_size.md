---
title: "Pen drive shows wrong size"
date: 2011-04-12
forum: General Help
---

### Post by krige on 2011-04-12
Hello,

I have a 16GB Corsair Flash Voyager GT pen drive. It worked fine for some time but recently, I am not sure for what reason, it is showing to have only 7.56GB of space.

Is it possible to fix this or is it the pen drive physically damaged?

---

### Post by matt_symes on 2011-04-12
Hi

> **krige said:**
> Hello,

I have a 16GB Corsair Flash Voyager GT pen drive. It worked fine for some time but recently, I am not sure for what reason, it is showing to have only 7.56GB of space.

Is it possible to fix this or is it the pen drive physically damaged?

If you format it do you get all the space back ?

Is it possible you deleted some files by sending them to the trash folder but not permanently deleting them ?

If you insert the usb device and automount it, open a terminal and type

```
du  /media/<name_of _usb_mount_point> | less
```

it will give you a summary of what files it thinks are on the drive. Use up and down arrows to scroll and press q to quit.

Also 

```
df  /media/<name_of _usb_mount_point>
```

will give you a summary of the amount of disk space used.

Kind regards

---

### Post by krige on 2011-04-12
matt_symes, thanks for your help!

I don't know what I did, but after trying formatting and partitioning a few times with GParted, an extra 8GB magically appeared on the drive.

I repartitioned the drive to fill in the 16GB and formatted to fat32. Now when I plug it in it is not automatically mounted. The /media/ directory is empty.

Any idea why is that?

---

### Post by matt_symes on 2011-04-12
Hi

Try giving the usb stick a label. That might help.

Kind regards

---

### Post by krige on 2011-04-12
> **matt_symes said:**
> Try giving the usb stick a label. That might help.

It worked, thanks a lot!!! :)

Any idea why this problem happened and how I can prevent it from happening again?

---

### Post by plucky on 2011-04-12
> **krige said:**
> It worked, thanks a lot!!! :)

Any idea why this problem happened and how I can prevent it from happening again?

If you delete files on the USB stick,always remember to empty the wastebasket before un-mounting the stick so the empty space will be recovered.

Good Luck

---

### Post by krige on 2011-04-13
> **plucky said:**
> If you delete files on the USB stick,always remember to empty the wastebasket before un-mounting the stick so the empty space will be recovered.

Sorry, it's my fault I didn't explain it properly. I was talking about the actual size of the partition, not about free space or taken space. 

Anyway, the pen drive again stopped working and shifted back to 8GB. I guess it must be some kind of hardware failure. The drive seems working ok with 8GB, so I guess I'll have to be content with that :/

---

### Post by matt_symes on 2011-04-13
Hi

> **krige said:**
> Anyway, the pen drive again stopped working and shifted back to 8GB. I guess it must be some kind of hardware failure. The drive seems working ok with 8GB, so I guess I'll have to be content with that :/

That is really odd. Can you try it in another computer ? If you open a terminal and type...

```
sudo fdisk -l
```

(Small L above. Enter your password. It will not be echoed to the screen) What does that return ?

Kind regards

---

### Post by krige on 2011-04-13
> **matt_symes said:**
> If you open a terminal and type...

```
sudo fdisk -l
```

(Small L above. Enter your password. It will not be echoed to the screen) What does that return ?

```
Disk /dev/sdf: 8120 MB, 8120172544 bytes
250 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15500 * 512 = 7936000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70707573

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   ?      109807      234729   968143376    d  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(255, 105, 46) logical=(109806, 87, 57)
Partition 1 has different physical/logical endings:
     phys=(370, 10, 5) logical=(234728, 19, 24)
Partition 1 does not end on cylinder boundary.
/dev/sdf2   ?      109807      144911   272054928    a  OS/2 Boot Manager
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(781, 111, 63) logical=(109806, 46, 34)
Partition 2 has different physical/logical endings:
     phys=(357, 80, 50) logical=(144910, 11, 59)
Partition 2 does not end on cylinder boundary.
/dev/sdf3   ?      114135      228288   884685616+  6f  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 51) logical=(114134, 162, 47)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 48) logical=(228287, 158, 27)
Partition 3 does not end on cylinder boundary.
/dev/sdf4   ?      186173      186177       26849    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 114, 37) logical=(186172, 244, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(186176, 110, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by matt_symes on 2011-04-13
Hi

That does not look right to me at all.

You could well be right that the drive is damaged. I would try to download a pen drive checker and see what that says. If you cannot find one for Linux try one for windows and run it in Wine.

Kind regards

---

### Post by krige on 2011-04-14
> **matt_symes said:**
> I would try to download a pen drive checker and see what that says.

I have tried to run:
```
sudo fsck -ar /dev/sdb
```

And this is what I got:
```
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
```

Should I choose option 1 or 2?!

---

### Post by matt_symes on 2011-04-14
Hi 

Make sure you have backed up any data on the pen.

Choose Option 2.

Kind regards

---

### Post by krige on 2011-04-21
The operation didn't solve the problem. I contacted Corsair support using their online form for the device replacement:
[http://www.corsair.com/support/technicalsupport](http://www.corsair.com/support/technicalsupport)

---

### Post by krige on 2011-05-05
Same problem happened again with another pen drive of another brand: its partition was 8GB and recently became 4GB. Could it be just a coincidence?

sudo fdisk -l
```
Disk /dev/sdf: 4029 MB, 4029677568 bytes
233 heads, 63 sectors/track, 536 cylinders
Units = cylinders of 14679 * 512 = 7515648 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099607

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         537     3934208    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(489, 232, 63) logical=(536, 39, 63)
```

sudo fsck -ar /dev/sdf
```
fsck from util-linux-ng 2.17.2
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdf
/dev/sdf: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

sudo e2fsck -b 8193 /dev/sdf
```
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

sudo fsck -ar /dev/sdf1
```
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
/dev/sdf1: 1 files, 1/981630 clusters
```

---

### Post by matt_symes on 2011-05-06
Hi

To run fsck you need to specify a partition like you did in your last example in your last post.

If the drive is being resized from 8G to 4G then something strange is going on.

Do you still get the same issue if you format it with NTFS or extX ?

Kind regards

---

