---
title: "Ext3 boot disk clone challenge"
date: 2009-08-08
forum: General Help
---

### Post by yonkiman on 2009-08-08
My boot disk apparently has a bad block somewhere.  I know this because when I try to clone it with dd, dd gets to a bad block and quits ("Input/output error").  When I try to clone it with "dd conv=noerror,sync", it completes the operation, but the cloned disk is unbootable - it seems to have something seriously wrong.

However I've been using this "bad" boot/system drive for a year with no errors in normal operation, and fsck sees nothing wrong it at all:
```
ubuntu@ubuntu:~$ sudo fsck -f /dev/sdf1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdf1: 227091/9625600 files (1.6% non-contiguous), 12789815/38497756 blocks
```

So I really want to clone it and put it on a new disk that doesn't have any bad blocks so I can start backing it up, updating the distribution without fear because I don't have a backup, etc.

I know I *could* do a fresh install, but it took me months (I'm a linux noob and don't have enough spare time) to get MythTV and my remote control optimized, my RAID array working, and all the other various tweaks going.  So I really, really want to somehow clone this disk.  I'd be willing to do some pretty tedious work if it would get me to a bootable clone (UUID cloned as well) of my original disk.

To summarize, here's what I've tried:
[LIST]
[*]dd - fails on bad blocks
[*]dd conv=noerror,sync - resulting disk is a mess
[*]cp /dev/sdf /dev/sde - had high hopes, but it seemed to gag on the bad block, too.
[*]I just ran "sudo e2fsk -c /dev/sdf1" on the problem drive, and it said it updated my bad block inode.  However when I ran dd it stopped at the same bad block. 
[/LIST]

Any other ideas?

---

### Post by louieb on 2009-08-08
try one of the parted programs like partimage. partimage just coppies the data to its image file. the do a restore to the new drive from it. [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") 

another one to try is Gparted [GPARTED DOCUMENTATION - COPYING]("http://gparted.sourceforge.net/larry/move/move.htm")

I know partimage copies the uuid - can't remember about Gparted - but that can be fixed with tune2fs. 

Then when done copying use the same CD to put GRUB on the MBR of the new drive. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")  (same fix will work for you)


and last only because I've never had to use it is [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html")

---

### Post by yonkiman on 2009-08-09
Thanks, louieb, but none of the dd-based or parted solutions worked, and I spent a long time trying to get partimage installed and then trying to get it to work before I gave up on it.

The final solution turned out to be relatively simple.  I used "cp -a" to copy all the files on the old drive over to a clean, bootable partition, then I edited the UUIDs in the /boot/grub/menu.lst file to be the same as the UUID of the new disk!  Almost too easy after months (off and on) of trying other ways (mostly dd-based).

Here's what I did in more detail (for newbies like me):

[LIST]
[*]Booted off of a 9.04 live CD with both my original problem drive (/dev/sdf) and the new drive I wanted to clone the original drive to (/dev/sde) attached.
[*]To make sure the disk was bootable, grub was installed, etc., I installed Ubuntu 9.04 on the new disk (sde). (There's probably a faster way to accomplish this but I knew this would do the trick.)
[*]Mounted sdf as disk-1, sde as disk-2
[*]Deleted all the files off the new install on disk-2
[*]Mounted sdf as disk-1, sde as disk-2
[*]sudo cp -a /media/disk-1/* /media/disk-2 (copies all the files recursively and keeps attributes and permissions)
[*]sudo blkid (Gets list of the UUIDs of all the disks. Manually copy the UUID for the new (sde) partition to the clipboard)
[*]sudo gedit /boot/grub/menu.lst (Now change the UUIDs in the grub entries from the ones for sdf (old) to the ones for sde (new) by pasting in the previously copied UUID)
[*]Rebooted, and it worked! Hallelujah!
[/LIST]

---

### Post by louieb on 2009-08-10
Nice you got it copied over and it worked. 
And thanks for **cp -a** tip. Hope I remember it next time I'm dealing with a similar situation.

---

