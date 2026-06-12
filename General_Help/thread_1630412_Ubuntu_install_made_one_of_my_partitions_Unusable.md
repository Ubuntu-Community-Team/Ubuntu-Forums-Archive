---
title: "Ubuntu install made one of my partitions Unusable"
date: 2010-11-25
forum: General Help
---

### Post by SheikhAmanAlam on 2010-11-25
Hello all.
I recently installed Ubuntu 9.04 and later it got updated to 10.04 via automatic upgrades.

Previously, I having Windows.
My HDD had 3 partitions.
I installed Ubuntu in the C drive of Windows partition, left D drive as it was (in NTFS, because it had crucial data), and wanted to extract some part of E to be used as Swap.
I marked E to be used as swap, but it took all of the drive as swap space, and later when I corrected it so that it takes only 2 Gigs and went ahead with the install, it made that partition unusable.

Maybe because it doesn't allow more than 4 physical partitions.

Help me out in this situation.

I am attaching two screenshots of Disk Utility results and Disk Part too.

Disk Utility Report:
--------------------

[IMG]http://s3.amazonaws.com/twitpic/photos/full/198160659.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1290681277&Signature=St1dKImONvb%2BjHf4oEQ5tsjPg1s%3D[/IMG]


GParted view:
-------------

[IMG]http://s3.amazonaws.com/twitpic/photos/full/198161215.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1290681397&Signature=F%2BGFKiEDy4PQaRts8asaap2xtd8%3D[/IMG]

Please suggest something.

---

### Post by dino99 on 2010-11-25
i'm feeling that you use wubi, right ? If so, dont expect serious result, wubi is not designed for working. To make a real install:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

note: cant check your screenshots (not loaded)

---

### Post by SheikhAmanAlam on 2010-11-26
I didn't use wubi at all.
I was using Windows and migrated to Ubuntu with a clean install at the first shot.

Here are the links to the images:

DiskUtility: [http://twitpic.com/39z9qr/full](http://twitpic.com/39z9qr/full)

GParted: [http://twitpic.com/39za67/full](http://twitpic.com/39za67/full)

I am having crucial data on my drives and may not have enough time to go through the installation all over again. at least in near future.

Is there any way I can correct the issues without going through all the hassles?

---

### Post by sikander3786 on 2010-11-26
The best method to create the swap partition would've been to either shrink your E drive first and then assign the freed up space to swap or to give it some space from your current / partition as that is more than a 100GB.

Anyways, now you've got some unallocated space on your drive. If E had some data on it, it might still be there. You can try testdisk to recover it.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

There are some more recovery options in the first link also.

And if that didn't contain any important data, you can just create an Extended partition in that space and then you'll be able to create even more than one logical partitions inside the extended one.

---

### Post by SheikhAmanAlam on 2010-11-29
Hi.
Thanks for guiding.
GParted tells me that I already have 4 partitions. and in order to create any extended partition, I might have to delete one primary partition.
see the attached screen shot of the error message.

What should be done in this case?
the screenshot of GParted, showing the current state of my drives, can be found in one of the replies made by me above.

---

### Post by sikander3786 on 2010-11-29
You already have 4 primary partitions. In order to create an extended partition, you'll need to delete one of the primary partitions and then can create extended/logical partitions.

Didn't you create those 4 partitions yourself?

Please post the output of

```
sudo fdisk -l
```

---

### Post by jocko on 2010-11-29
Just delete the swap partition, make an extended partition to fill up the rest of the drive and then create a new swap partition in the extended partition.

But if you had any valuable data in the E:\ partition, you need to try to recover that before you do anything than could overwrite the data.

---

### Post by SheikhAmanAlam on 2010-11-29
This is the output of fdisk:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13417   107667456   83  Linux
/dev/sda3           13417       27440   112638976    7  HPFS/NTFS
/dev/sda4           27441       27689     2000092+  82  Linux swap / Solaris
```


I didn't create those 4 partitions.
That's the problem, i was given the system after the installation :-P
I am gonna try out what **jocko** said.
i don't care about the data in E.

---

### Post by SheikhAmanAlam on 2010-11-29
Wow.. it worked like a charm!
**Jocko**'s method worked, and now I can access my "E" drive of windows very well.
There was no data in it, so I don't care about it, If i did, I could have tried TestDisk and so.

Thanks people.

---

