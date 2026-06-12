---
title: "Gparted error upon resizing partition"
date: 2012-04-24
forum: General Help
---

### Post by astrobob.tk on 2012-04-24
Hello,

I am in need of your help!

I logged in to my system which I made to automount the partition /dev/sda9 (/Data). Earlier I did a resize of this partition when installing Pangolin for testing. In an attempt to increase the size of the testing system, and while logged in my default system (Lucid), I closed all applications that are using /Data, umount(ed) /dev/sda9 & used gparted to resize /dev/sda9 (I know; I should have used a live session instead so I am sure all partitions are unmounted; my bad!!)

So the thing is that gparted produced an error (attached):

```
GParted 0.5.1
 Libparted 2.2
    **Shrink /dev/sda9 from 125.12 GiB to 120.25 GiB**  00:00:15    ( ERROR )             calibrate /dev/sda9  00:00:00    ( SUCCESS )             [I]path: /dev/sda9
start: 161887068
end: 424275739
size: 262388672 (125.12 GiB)[/I]          check file system on /dev/sda9 for errors and (if possible) fix them  00:00:07    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda9***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   14413 inodes used (0.18%)
    1725 non-contiguous files (12.0%)
       2 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 12877/241
24318123 blocks used (74.14%)
       0 bad blocks
       3 large files

   11709 regular files
    1410 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
    1285 symbolic links (1285 fast symbolic links)
       0 sockets
--------
   14404 files
[/I]       [I]e2fsck 1.41.11 (14-Mar-2010)
[/I]             shrink file system  00:00:03    ( SUCCESS )             ***resize2fs /dev/sda9 126086120K***             [I]Resizing the filesystem on /dev/sda9 to 31521530 (4k) blocks.
The filesystem on /dev/sda9 is now 31521530 blocks long.

[/I]       [I]resize2fs 1.41.11 (14-Mar-2010)
[/I]             shrink partition from 125.12 GiB to 120.25 GiB  00:00:02    ( SUCCESS )             [I]old start: 161887068
old end: 424275739
old size: 262388672 (125.12 GiB)[/I]       [I]new start: 161887068
new end: 414059309
new size: 252172242 (120.25 GiB)[/I]          check file system on /dev/sda9 for errors and (if possible) fix them  00:00:01    ( ERROR )             ***e2fsck -f -y -v /dev/sda9***             [I]The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

[/I]       [I]e2fsck 1.41.11 (14-Mar-2010)
[/I]             grow file system to fill the partition  00:00:02    ( ERROR )             ***resize2fs /dev/sda9***             [I]Resizing the filesystem on /dev/sda9 to 31521530 (4k) blocks.
[/I]       [I]resize2fs 1.41.11 (14-Mar-2010)
resize2fs: Can't read an block bitmap while trying to resize /dev/sda9 
Please run 'e2fsck -fy /dev/sda9' to fix the filesystem
after the aborted resize operation.
[/I]             ========================================
    **Move /dev/sda10 to the left and grow it from 4.75 GiB to 9.63 GiB**    ========================================

```I seek your help.

For more info, here's the fdisk output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72078d5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       10077    65539869+   7  HPFS/NTFS
/dev/sda4           10078       60802   407443027    5  Extended
/dev/sda5           27032       31238    33788928    7  HPFS/NTFS
/dev/sda6           31239       31846     4882432   82  Linux swap / Solaris
/dev/sda7           31847       34886    24413184   83  Linux
/dev/sda8           34886       60802   208168960   83  Linux
/dev/sda9           10078       25774   126086121   83  Linux
/dev/sda10          25775       27031    10096821   83  Linux

Partition table entries are not in disk order

```P.S.: When rebooting, Ubuntu tried checking the partition but it lead to nowhere; I had to skip mounting it.

---

### Post by oldfred on 2012-04-24
It says at the end to do this, did you? And best to run from liveCD.

[I]e2fsck -fy /dev/sda9

Any logical partition mounts the extended partition and you cannot modify any logicals as extended is mounted. This is why even with liveCD you often have to do swap-off as swap is usually a logical partition.
[/I]

---

### Post by ph4nt0m117 on 2012-04-24
It is impossible to resize a partition AFTER installing.

If you want a bigger space, get more hard drives.  Obviously your current one is enormous.

Or get a USB drive.

---

### Post by cortman on 2012-04-24
> **ph4nt0m117 said:**
> It is impossible to resize a partition AFTER installing.

If you want a bigger space, get more hard drives.  Obviously your current one is enormous.

Or get a USB drive.

THIS is pure nonsense. I myself have resized countless partitions after reinstalling.

---

### Post by astrobob.tk on 2012-04-24
> **oldfred said:**
> It says at the end to do this, did you? And best to run from liveCD.

[I]e2fsck -fy /dev/sda9

Any logical partition mounts the extended partition and you cannot modify any logicals as extended is mounted. This is why even with liveCD you often have to do swap-off as swap is usually a logical partition.
[/I]

No didn't. Just did it from Knoppix usb:

```
$ e2fsck -fy /dev/sda9 
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes

```

Also tried without the 'y' option:

```
 e2fsck -f /dev/sda9
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 31981568 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

e2fsck: Can't read an block bitmap while retrying to read bitmaps for Data
e2fsck: aborted
```


I ran a Knoppix from a usb & tried mounting (in nautilus) the partition. I got an error that said that "dmesg | tail" might help, so here it is:

```
$ dmesg | tail
[   38.461845] drm: registered panic notifier
[   38.461858] [drm] Initialized radeon 2.7.0 20080528 for 0000:01:00.0 on minor 0
[   39.636262] Adding 4882428k swap on /dev/sda6.  Priority:-1 extents:1 across:4882428k 
[   51.976178] NET: Registered protocol family 10
[   51.976344] lo: Disabled Privacy Extensions
[   59.727755] tg3 0000:08:00.0: irq 44 for MSI/MSI-X
[   59.755260] lp: driver loaded but no devices found
[   59.760127] ppdev: user-space parallel port driver
[   59.828919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  112.890736] EXT4-fs (sda9): bad geometry: block count 32798584 exceeds size of device (31521530 blocks)

```Moreover, here is the fsck output:

```
$ sudo fsck /dev/sda9
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Data contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 31981568 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

fsck.ext4: Can't read an block bitmap while retrying to read bitmaps for Data
e2fsck: aborted


```

---

### Post by oldfred on 2012-04-24
I think gparted wanted you to run the e2fsck as the partition data is corrupted or just the error that e2fsck is now saying. You have to have partition table data and internal data match.

#From liveCD so everything is unmounted,swap off if necessary
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda9
#if errors:
sudo e2fsck -f -y -v /dev/sda9

And if that does not work, but this is grasping at straws. I never have had to do any of this:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by astrobob.tk on 2012-04-25
> **oldfred said:**
> I think gparted wanted you to run the e2fsck as the partition data is corrupted or just the error that e2fsck is now saying. You have to have partition table data and internal data match.

#From liveCD so everything is unmounted,swap off if necessary
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda9
#if errors:
sudo e2fsck -f -y -v /dev/sda9


```
$ sudo e2fsck -C0 -p -f -v /dev/sda9
Data: The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!


Data: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

$ sudo e2fsck -f -y -v /dev/sda9
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes


$ sudo e2fsck -f -v /dev/sda9
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 31981568 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

e2fsck: Can't read an block bitmap while retrying to read bitmaps for Data
e2fsck: aborted
```> **oldfred said:**
> 
 And if that does not work, but this is grasping at straws. I never have had to do any of this:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)


This helped solve the problem :D:

```
$ sudo fsck.ext4 -v /dev/sda9
e2fsck 1.41.12 (17-May-2010)
The filesystem size (according to the superblock) is 32798584 blocks
The physical size of the device is 31521530 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Data contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 31981568 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

fsck.ext4: Can't read an block bitmap while retrying to read bitmaps for Data
e2fsck: aborted
``````

$ sudo mke2fs -n /dev/sda9
mke2fs 1.41.12 (17-May-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7880704 inodes, 31521530 blocks
1576076 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
962 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872
``````
$ sudo e2fsck -b 23887872 /dev/sda9

```Interrupted it at some point since I chose the last (?) backup?  And ran:

```
$sudo e2fsck -b 32768 /dev/sda9
.
.
.
Data: ***** FILE SYSTEM WAS MODIFIED *****
Data: 14413/7880704 files (12.0% non-contiguous), 24298077/31521530 blocks
```> **oldfred said:**
> 
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5


This was not tried!

> **oldfred said:**
> One user could not get partition unmounted (may have needed swapoff), but used another live distro

Thank you; now I know :D

Thank you for you help; I appreciate it :D

---

### Post by oldfred on 2012-04-25
Glad the backup super block worked.

---

