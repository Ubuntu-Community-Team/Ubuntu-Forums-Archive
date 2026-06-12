---
title: "Messed up partitions - can't mount"
date: 2010-03-16
forum: General Help
---

### Post by berniev on 2010-03-16
I was so happy with Linux I decided to move almost everything away from windows.

I did a dumb thing - having moved all my important data to linux, I used partition magic from within XP to shrink my ntfs partition. It crashed out when nearly done, but now I can't mount linux partition.

booted from ubuntu 9.1 CD .....

root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd42ad42a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       19457   130688775    f  W95 Ext'd (LBA)
/dev/sda5            9561       15361    46596469+  83  Linux
/dev/sda6           19284       19457     1397623+  82  Linux swap / Solaris


root@ubuntu:/home/ubuntu# sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 51199092, Id= 7, bootable
/dev/sda2 : start= 51199155, size=261377550, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=153581464, size= 93192939, Id=83
/dev/sda6 : start=309781458, size=  2795247, Id=82

root@ubuntu:/# mkdir /mnt/sda5
root@ubuntu:/# mount /dev/sda5 /mnt/sda5
mount: you must specify the filesystem type
root@ubuntu:/# 

Does being able to see the partitions mean there is some chance of fixing this? (Fingers crossed)

---

### Post by Rocket2DMn on 2010-03-16
Try specifying the filesystem type:
```
sudo mount -t ext3 /mnt/sda5
```
Does that mount?

---

### Post by berniev on 2010-03-16
I (thought) it was ext4 not ext3. Does that matter?

---

### Post by berniev on 2010-03-16
tried it anway

mount -t ext3 /dev/sda5 /mnt/sda5
mount: wrong fs type, bad option, bad superblock ....etc

Gparted can't identify the file system type either - unknown

---

### Post by Rocket2DMn on 2010-03-16
Yes, it can be ext4, I guess I'm behind the times, sorry.  Ext4 is the default nowadays with Ubuntu - try that.

---

### Post by berniev on 2010-03-16
same result :(

---

### Post by srs5694 on 2010-03-16
Try "e2fsck /dev/sda5" from your emergency system. I'm not hopeful this will work, but it might. It's also possible that the testdisk utility could help.

Background: I see two possible root causes. The first is that Partition Magic changed the start location of the Linux partition without actually changing anything in the ext4fs filesystem it contains. If this is the case, recovery is theoretically possible, but it's a question of finding the start of the filesystem data and altering the partition data to match. This is what testdisk can do. (I'm not positive it will move the start and end points of an existing partition, though; it might be necessary to delete the Linux partition to get this to work -- an odd-sounding proposition!) The second cause I can imagine is that Partition Magic wrote bad data in the Linux partition. This error might be corrected by e2fsck -- or if PM's damage was too great, e2fsck won't be able to do anything about it.

---

### Post by berniev on 2010-03-16
root@ubuntu:/# e2fsck /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/#

---

### Post by prodigy_ on 2010-03-16
> **berniev said:**
> try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
What it suggests is, generally, right. Only the next superblock might be not at 8193. You'll need testdisk to identify superblocks correctly.

---

### Post by srs5694 on 2010-03-16
You could try running the suggested command to use the alternate superblock, but this isn't looking good. My guess is that either PM has really badly damaged the filesystem or it's shifted the carrier partition's location. The latter will probably be easier to repair, if testdisk can find the true start point of the filesystem. (I've only done a few experiments with testdisk, so I can't provide detailed suggestions on how to use it. I recommend you read [its documentation](http://www.cgsecurity.org/wiki/TestDisk).)

---

### Post by berniev on 2010-03-17
Well a big thankyou to you!

I was reticent to use Testdisk, what with it not appearing to support ext4 and not many references to it after extensive Googling.

I tried all the backup superblock locations - no good.

So I tried the supposed 'last ditch' approach mke2fs-S to rebuild the superblocks.
It reported job done. But still wouldn't mount and I noticed usage on sda5 was way smaller than I would expect, so figured this was still not right.

Finally downloaded beta version of testdisk (which is actually photorec), extracted the contents, and from terminal ran testdisk_static.
After stumbling through a few simple menus, including telling it to operate read-only, it ran and offered to write the partition tables. Holding my breath I agreed.
Still wouldn't mount.
Rebooted back into ubuntu cd and voila! There was my linux partition. And it mounted manually immediately! Unlike experiences of some others I had read about it appears to be 100%. Lost&Found is empty.

I know I'll have  bit more work to do on this but the data is back so hopefully you won't hear from me again!

Thankyou again for saving my skin by pointing me in the right direction. This has been an interesting 24 hours and it was looking increasingly likely that I was faced with total data loss.


Bernie

---

### Post by srs5694 on 2010-03-17
I'm glad to hear it worked for you. Now for the next step: Create a backup of your partition table to avoid such problems in the future. There are several ways you can do this, but the single most flexible is to use the sfdisk program:

```

sudo sfdisk -d /dev/sda > sda-backup.txt

```

The resulting file, sda-backup.txt, holds a text-mode description of all your partitions. If the same problem were to occur again, you could easily restore them:

```

sudo sfdisk /dev/sda < sda-backup.txt

```

Be sure to store the backup on some medium other than the disk itself, of course, such as a USB flash drive, a CD-R, a floppy disk, or a network file share.

---

