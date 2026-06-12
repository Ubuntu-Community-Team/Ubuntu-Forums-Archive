---
title: "Mounting NTFS drive after Windows Failure"
date: 2011-02-01
forum: General Help
---

### Post by psuliin on 2011-02-01
I've been working for a while to help a friend re-activate her system after a Windows crash.  I tried every way I could to restore Windows, but the system is thoroughly bollixed.  The data is still there on the disk, and you can read/write if you boot off of external media. I backed up her data that way.

Details if you need them, but for now suffice it to say that I finally got her up and running by installing Xubuntu Lucid in a dual-boot setup.  However Xubuntu isn't automatically recognizing and mounting the NTFS partition the way I would expect it to.  I had her run a few commands in the terminal, and here's what she got.

Output from **sudo fdisk -l**:
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4f3b4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5463    43876678+   7  HPFS/NTFS
/dev/sda2            5463       10012    36540417    5  Extended
/dev/sda5            5463        9819    34993152   83  Linux
/dev/sda6            9820       10012     1546240   82  Linux swap / Solaris
```

So her NFTS partition is there, under /dev/sda1.  However this is what she gets from **cat /etc/fstab**:

```
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7123baee-433a-4cc4-bcf7-1af95510138a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=19199c82-e5f1-414d-b855-70de283cb336 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

If i'm reading this right, there is no mount point in fstab for the NTFS partition.  Which seems a bit odd.  

Ordinarily I'd use **mkdir** then **mount** to solve this. But I'd like to check a few things before I go and do that.

First, as I understand it if a Windows instance is not shut down properly it can make it difficult for Linux to mount the partition.  The usual solution is simply to reboot Windows and then shut down properly, but that's impossible in this case.  Will that affect the **mkdir/mount** solution?

Second, the fact that /dev/sda1 doesn't even show up in fstab causes me some concern.  Would that be a problem for **mkdir/mount**?

And third, how to I set it up so the NTFS partition mounts automatically?

---

### Post by mikewhatever on 2011-02-01
> **psuliin said:**
> ...

First, as I understand it if a Windows instance is not shut down properly it can make it difficult for Linux to mount the partition.  The usual solution is simply to reboot Windows and then shut down properly, but that's impossible in this case.  Will that affect the **mkdir/mount** solution?

It might, but since you could read and write to it, there shouldn't be a problem.

> Second, the fact that /dev/sda1 doesn't even show up in fstab causes me some concern.  Would that be a problem for **mkdir/mount**?

And third, how to I set it up so the NTFS partition mounts automatically?

Internal partitions are not automounted by default, and fstab entries are not created for them. Presumably, it's assumed that automounting is not required, and if it was, the user would set it up during the installation.
If you think your friend needs it automounted, add the following to fstab and create the mount point.
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by Mark Phelps on 2011-02-01
IF the NTFS partition was not cleanly shutdown, then Ubuntu may consider it "dirty" and refuse to mount it -- regardless of the method you take.

I would first see if you can access it via Places.  

IF that won't mount it, my guess would be that you'll have to somehow run chkdsk against it in an MS Windows environment before the partition can be mounted again.

---

### Post by Rhizoid on 2011-02-01
I'd do it like this (usual disclaimer re this not being the only way, there may be other and or better ways and that this way might be "wrong" - also you may know this already and would granny like another egg?)

Open a terminal.
Find the UUID of /dev/sda1 by issuing:

```
sudo blkid | grep sda1
```Select the UUID indside the quotes with the mouse, right click and copy

```
sudo gedit /etc/fstab
```At the end of the fstab file create a new entry to auto mount the NTFS partition

```
UUID={paste previously copied UUID here and remove the curly brackets}    /mnt/sda1    ntfs    defaults    0    0
```IMPORTANT: Create the mount point shown in fstab

```
sudo mkdir /mnt/sda1
```Test that it works:

```
sudo mount -a
ls -alF /mnt/sda1
```Obviously you can take your pick of mount point, /mnt/sda1 is a little bland and not very descriptive unless your beany hat has a propeller on it like mine does :)

---

### Post by Rhizoid on 2011-02-01
Forgot to mention - a dirty ntfs partition can sometimes be cleaned using ntfsfix, negating the need to restart windows an run chkdsk.

(ensure you've backed up the drive and any important data first etc.)

---

### Post by psuliin on 2011-02-01
> **Mark Phelps said:**
> I would first see if you can access it via Places.  

IF that won't mount it, my guess would be that you'll have to somehow run chkdsk against it in an MS Windows environment before the partition can be mounted again.

Mark, if it doesn't have a mount point then how would Places find it?

---

### Post by Mark Phelps on 2011-02-01
> **psuliin said:**
> Mark, if it doesn't have a mount point then how would Places find it?

The mount point is something you specify when you go to mount a partition.

From what I recall, Places will generate its own default mount points based on the partitions it can find in your machine.

I believe they're usually under "Media".

---

### Post by psuliin on 2011-02-03
Well, I have good news and bad news.

The bad news is that I won't have a chance to try any of the suggestions on this thread.

The good news is that I don't need to.  My friend decided to cut her Windows tether completely and asked me to help her reformat her NTFS partition to ext4.  We'd already backed up her critical data, and she wanted the space.

---

