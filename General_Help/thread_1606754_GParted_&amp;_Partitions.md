---
title: "GParted &amp; Partitions"
date: 2010-10-26
forum: General Help
---

### Post by amorphouskev on 2010-10-26
Setup: Ubuntu 10.10 500gig drive. 

I loaded the live CD, used GParted to create a partition of 96.42gig because I was curious to see if I could install OS X on that particular partition. However GParted said there was an error while trying to complete, but it looked like everything went through without any issue so I restarted and tried to install OS X. It of course didn't see a single drive.

After removing the disk and attempting to reboot to good ol' Ubuntu I was bombarded with a black screen and a bunch of text basically telling me it couldn't load Ubuntu. So back into the Live CD I'm attempting to change the format of my unallocated partition or just get rid of it. Here's a shot of GParted:

[[IMG]http://img100.imageshack.us/img100/2685/screenshotvi.th.png[/IMG]]("http://img100.imageshack.us/i/screenshotvi.png/")

Also, when I attempt to access my drive via live CD this is what I get:

[[IMG]http://img818.imageshack.us/img818/4898/screenshot1be.th.png[/IMG]]("http://img818.imageshack.us/i/screenshot1be.png/")

Can anyone tell me how to get back to square 1 where everything was working well before I messed it all up?

Thanks.

---

### Post by dcstar on 2010-10-27
> **amorphouskev said:**
> Setup: Ubuntu 10.10 500gig drive. 

I loaded the live CD, used GParted to create a partition of 96.42gig because I was curious to see if I could install OS X on that particular partition. However GParted said there was an error while trying to complete, but it looked like everything went through without any issue so I restarted and tried to install OS X. It of course didn't see a single drive.

After removing the disk and attempting to reboot to good ol' Ubuntu I was bombarded with a black screen and a bunch of text basically telling me it couldn't load Ubuntu.
..........

Use gparted to do a "check" of the Ubuntu partition.

---

### Post by amorphouskev on 2010-10-27
> **dcstar said:**
> Use gparted to do a "check" of the Ubuntu partition.

When I do that, I get an message that says

An error occurred while applying the operations
See the details for more information.

But it doesn't tell me what the errors are.

Random additional info:

when trying sudo fdisk -lu, I get this:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00045dcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   751584959   375791456   83  Linux
/dev/sda2       953792510   976773119    11490305    5  Extended
/dev/sda5       953792512   976773119    11490304   82  Linux swap / Solaris

---

### Post by oldfred on 2010-10-27
I would first try:

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by amorphouskev on 2010-10-27
> **oldfred said:**
> I would first try:

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

Ok, I tried: sudo e2fsck -C0 -p -f -v /dev/sda1   and got:

> /dev/sda1: The filesystem size (according to the superblock) is 93948112 blocks
The physical size of the device is 93947864 blocks
Either the superblock or the partition table is likely to be corrupt!So then I tried this command (which I think is the correct one?): sudo fsck /dev/sda1

> fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 93948112 blocks
The physical size of the device is 93947864 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 280828/23494656 files (0.7% non-contiguous), 41326981/93948112 blocks

---

### Post by srs5694 on 2010-10-27
I recommend doing this:


[list=1]
[*]Enter fdisk ("sudo fdisk -u /dev/sda").
[*]Type "p" to display your partition table. Verify it's as you've posted here. If not, abort by typing "q" and figure out what's wrong.
[*]Type "d" and delete partition 1.
[*]Type "n" to create a new partition. Make it a primary partition (#1), specify the same start sector as the partition 1 you just deleted, and set an end sector that's at least 1984 sectors beyond the original partition 1's end point.
[*]For completeness, type "a" and set the active/boot flag on the new partition #1. (This isn't really necessary, but it won't hurt, and it will make the new partition more like the original.)
[*]Type "p" to review the partition table again. It should look just like the one you've posted except that partition #1 should have a different (later) end point. If not, and especially if the start sector doesn't match, either go back to step #3 or abort by typing "q" and figure out what went wrong.
[*]If everything looks OK, type "w" to save your changes.
[/list]


This will effectively extend /dev/sda1 so that it's large enough to hold the filesystem. I recommend you run e2fsck again at this point, although it's conceivable that Linux will now boot. Running e2fsck seems advisable because there's a good chance that something has overwritten part of the last few sectors on /dev/sda1, which means there could well be some filesystem damage there. It's also possible you've lost some files, but with any luck that hasn't happened.

---

### Post by amorphouskev on 2010-10-27
> **srs5694 said:**
> I recommend doing this:

Type "d" and delete partition 1.

So this will completely delete EVERYTHING on that partition correct?

---

### Post by srs5694 on 2010-10-27
> **amorphouskev said:**
> [quote=srs5694]Type "d" and delete partition 1.So this will completely delete EVERYTHING on that partition correct?[/QUOTE]

No. It deletes the partition -- that is, the information that identifies where the partition begins and ends. The data in the partition will still exist; it will just exist in an unpartitioned space on the hard disk. The subsequent steps in the instructions I posted re-create the partition data, but you'll create a larger partition -- one that's large enough to contain the filesystem that's too large for the current partition. (Some utility you used seems to have inappropriately shrunk /dev/sda1 without adjusting the filesystem it contains, thus creating this problem.)

---

### Post by amorphouskev on 2010-10-27
> **srs5694 said:**
> No. It deletes the partition -- that is, the information that identifies where the partition begins and ends. The data in the partition will still exist; it will just exist in an unpartitioned space on the hard disk. The subsequent steps in the instructions I posted re-create the partition data, but you'll create a larger partition -- one that's large enough to contain the filesystem that's too large for the current partition. (Some utility you used seems to have inappropriately shrunk /dev/sda1 without adjusting the filesystem it contains, thus creating this problem.)

OMG thank you so much! Went through your steps - got a little nervous cuz I still had errors when I booted, but it did a disk check and booted right into ubuntu. Thank you!!

SOLVED!!!

---

### Post by prunus_dulcis on 2011-01-04
Sorry, wrong thread :)

Trying to solve an issue remotely similar to this over [here]("http://ubuntuforums.org/showthread.php?p=10315037")...

---

