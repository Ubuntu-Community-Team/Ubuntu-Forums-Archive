---
title: "Partitionproblems"
date: 2006-02-17
forum: General Help
---

### Post by RaptorRaider on 2006-02-17
I really hope someone can guide me through this fast.

I have major partitioningproblems weekly, if not daily.
The reason is simple: I have to maintain multiple Linux and Windows installations on one 500GB hard disc, and these installations often change or are replaced.
Most of the time, I can fix it using my head and a Knoppix CD.
Today however, I seem to have failed.

Today, I was able to remove many installations and reduce it to just one Ubuntu partition and two Windows XP partitions.

The large, 420GB XP partition has been there for ages. Didn't change that today.
The 10GB Ubuntu partition and 2GB swap partition were created today, but worked fine until I installed the second XP partition.
Not sure why, but whenever you install a second primary Windows partition on 1 disc, it automatically becomes a logical partition. Even though I didn't ask for that.
MBR however does point at the NTLDR of this logical partition, which does not work of course. Not that that matters much though - I need to reinstall GRUB anyway.

Usually, when adding another partition, old partitionnumbers change and you have to reconfigure boot.ini and /boot/grub/menu.lst and /etc/fstab yourself.
In the current state however it is useless to edit boot.ini, because I won't be able to use it anyway (Windows only boots when it is the first partition on the first hard disc, which is currently the unfinished and new XP partition). Plus both XP installations use NTFS.

So I try to recover GRUB, and edit /boot/grub/menu.lst and /etc/fstab.

For some reason, that seems impossible today.
I can't write anything to /dev/sda3 (the Ubuntupartition):
> mkdir: cannot create directory `/mnt/sda3/media/WindowsXP3': Read-only file system
Why, why is this a read-only filesystem?
Are my partitiontables screwed up?
If so, how am I supposed to repair them?

/dev/sda2 is swap.
/dev/sda3 is Ubuntu.
/dev/sda4 is old XP.
/dev/sda5 is new XP.

fdisk /dev/sda (print):
> The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5087    40853295    f  W95 Ext'd (LBA)
/dev/sda2            5088        5330     1951897+  82  Linux swap
/dev/sda3            5331        6546     9767520   83  Linux
/dev/sda4   *        6547       60800   435795223+   7  HPFS/NTFS
/dev/sda5               2        5087    40853263+   7  HPFS/NTFS
fdisk /dev/sda3 (print):
> Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 1216.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sda3: 10.0 GB, 10001940480 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

---

### Post by RaptorRaider on 2006-02-17
> Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel Building a new DOS disklabel.
Should've named this thread "partitiontable screwed up", eh?

How about I do a "fdisk /dev/sda3" and then a "w" since "w" does "write table to disk and exit"?


Edit:
Just tried the "w"-thingy, and it's not really working.

New fdisk /dev/sda3 is showing a change, but I still can't write to sda3 (after a reboot):
> The number of cylinders for this disk is set to 1216.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda3: 10.0 GB, 10001940480 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

---

### Post by RaptorRaider on 2006-02-17
Just did a reinstall of Ubuntu (yes, again), and that did not solve the problem of not being able to edit files from Knoppix, which is absolutely essential for me.

Could the following be the problem?
> The number of cylinders for this disk is set to 1216.

---

### Post by RaptorRaider on 2006-02-18
Just downloaded and burned Knoppix 4.02 but I still can't write anything to the Ubuntu-partition.

Again, the main questions are:
Why can't I write anything to my Ubuntu-partition from a LiveCD like Knoppix and how can I fix this?
How can I boot the new XP partition (after it is made primary of course, using Knoppix) which is not really "done" yet (e.g. can I boot an XP installation using boot.ini from another partition even though the XP installation in question does not have any bootsoftware)?

---

### Post by RaptorRaider on 2006-02-18
Great.
I couldn't even shut down Knoppix 4.02 the proper way; it hung at:
> Unmounting/Synching Filesystems /mnt/sda3

---

