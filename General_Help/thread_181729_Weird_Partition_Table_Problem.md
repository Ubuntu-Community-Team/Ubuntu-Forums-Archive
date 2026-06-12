---
title: "Weird Partition Table Problem"
date: 2006-05-24
forum: General Help
---

### Post by Itazura on 2006-05-24
Here's my story:

I have a 42.0 gig hard drive,  with an 8.0 gig NTFS partition for Windows, an 8.0 gig partiton for PuppyLinux,  and the remainder for Ubuntu Linux. I decided to play around with PCLinux OS and thought I would use Disk Drake from the live CD to create a new partition and install it. I attempted to resize the PuppyLinux Partition and create a new EXT3 partition with the leftover space. The resize failed and now when I run parted I get the following error:

Error opening /dev/hdc: No medium found

Also, when I run GParted the entire 42.09 gigs is shown as unallocated and the disk label type is shown as unrecognized. The return result for fdisk /dev/hdc is:

Unable to open /dev/hdc

Now here's the weird part: I am still able to boot into PuppyLinux, Windows and Ubuntu Linux with no problem. Additionally, the Media Utility Tool (MUT) in Puppy Linux shows all of my partitions and I can mount/unmount them from there, but I am unable to use the live GParted CD, fdisk, parted, Gparted (in Ubuntu) or any other tool to resize or even read my partitions. Obviously, all the partitions are there or I wouldn't be able to boot. Also, GRUB works fine. How to I recover my partition table? Is this even a partition table problem, or did I hose the MBR? Thanks in advance for your help/suggestions.

Itazura

Edit: here's my fdisk output:

Disk /dev/hda: 45.1 GB, 45191946240 bytes
255 heads, 63 sectors/track, 5494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1296    10410088+   7  HPFS/NTFS
/dev/hda2            2190        5401    25800390   83  Linux
/dev/hda3            1743        5494    30137940    5  Extended
/dev/hda4            1297        1742     3582495   83  Linux
/dev/hda5            1743        2189     3590496   83  Linux
/dev/hda6            5402        5494      746991   82  Linux swap / Solaris

Hope this helps with the mystery, thanks.....

---

### Post by Itazura on 2006-05-25
Hey, everybody,

I fixed the problem. Unbeknownst to me (a relative noob),  I cannot have more than 4 primary partitions on one drive ( or so GPArted tells me).  I was able ot fix the problem by booting up the PC LinuxOS CD, opening Drive Drake and reversing the process. Apparently I created an overlapping extended partition that was as latrge as the whole drive...oops! Anyway, thanks for being here.

Itazura

---

