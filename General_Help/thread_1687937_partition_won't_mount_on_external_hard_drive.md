---
title: "partition won't mount on external hard drive"
date: 2011-02-14
forum: General Help
---

### Post by rawlins02 on 2011-02-14
Been using a SeaGate FreeAgent external drive for past 6 months.  Suddenly the ext2 partition (/dev/sdb2) won't mount, while the NTFS partition (/dev/sdb1) does.  I've been allowing automount, no entry in /etc/fstab.  When the NTSF partition mounts there appears an entry in /etc/mtab:

/dev/sdb1 /media/FreeAgent\040Drive fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0


I added a line:

/dev/sdb2 /media/Ext2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

and then tried:  mount /dev/sdb2.   mount says /media/Ext2 does not exist.  Did that partition with all my data just go belly up?


EDIT new info:  fdisk -l shows

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfef64909

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           70609      121601   409601272+   7  HPFS/NTFS
/dev/sdb2               1       70608   567158728+  83  Linux

---

### Post by rawlins02 on 2011-02-15
Ideas?

If partition shows up in the table (fdisk), does that mean it's there?  Could I have lost data by possibly disconnecting the drive while mounted?  Should a 6 month old external drive not be trusted with data?

---

### Post by dabl on 2011-02-15
The partition should be fine -- use Gparted to fsck it if you want, or e2fsck. You should always use the "safely remove" option in your file manager to disconnect a USB storage device - you can certainly lose data if you don't.

As far as mounting, why are you twiddling with /etc/mtab settings?  AFAIK that is a system file that I've never touched in years of using USB memory sticks, card readers, and external hard drives. Try clearing out all the subdirectories under /media, and then just plug in the drive and wait for the notifier to pop up.

---

### Post by vanadium on 2011-02-15
In such a case, the first thing I would try to do is mount it manually using the terminal. An error message will reveal if there is a problem at the level of the partition or its file system. If not, then you know the problem is with gnome and the automount function.

---

### Post by rawlins02 on 2011-02-15
I've tried mounting.

mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Ran e2fsck.  I have a liveCD to try Gparted if needed.  For now have the disk utility tool open.  When I issued the e2fsck command the volume(?) changed from unknown and now shows as ext4. Can't mount in there.  Meanwhile, e2fsck shows:

Group descriptor 4327 checksum is invalid.  FIXED.
Group descriptor 4327 checksum is invalid.  FIXED.

repeatedly and then:

Ext4Partition contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Now a bunch of numbers are scrolling.....

---

### Post by rawlins02 on 2011-02-15
Partition recovered using e2fsck at command line.

dabl: I know about safely remove. Accidents happen.  Twiddled with /etc/mtab looking desperately for an answer.

---

### Post by jroa on 2011-02-15
For the mount, you may have to tell the computer what the drive format is.  For ext2, you should not have to, but I guess it is worth a try.

```
sudo mount -t ext2 /dev/sdb1 /mnt/dirname
```

Ext2 is not a journaling filesystem, so the drive may have become corrupted if the computer turned off during use.  You will have to run check disk.

For fstab, you could try the following.

```
/dev/sdb1        /mnt/dirname            ext2    defaults    1 1
```

---

### Post by dabl on 2011-02-15
The bad superblock error is probably what was keeping it from mounting automatically. Plus the need for an fsck.

If you want to get a little more elaborate with your USB device mounts, there are ways to do that with udev rules:

[http://kubuntuforums.net/forums/index.php?topic=3115658.msg255204;topicseen#msg255204](http://kubuntuforums.net/forums/index.php?topic=3115658.msg255204;topicseen#msg255204)

(udev works the same whether KDE or Gnome)

---

