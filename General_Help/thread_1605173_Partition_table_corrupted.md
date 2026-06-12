---
title: "Partition table corrupted"
date: 2010-10-25
forum: General Help
---

### Post by vishuindian on 2010-10-25
Dear all
         I am trying to install ubuntu 10.04 on my laptop. But at installation time its unable to show my existing hard disk partition table instead its only show option to create new partition table. Although by running ubuntu 10.04 directly from cd , i can see following partition table on my disk.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1288    10344837    5  Extended
/dev/sda2            1276        1288      104391   83  Linux
/dev/sda3            1289        3512    17864280   83  Linux
/dev/sda4            3513        9729    49938052+  83  Linux
/dev/sda5               1          13       96256   83  Linux
/dev/sda6              13         256     1951744   82  Linux swap / Solaris
/dev/sda7             256        1275     8188928   83  Linux
/dev/sda8            1275        1275        1406   83  Linux


Whats may be the reason? and how i can get my existing partition table at installation time.

Thanks

---

### Post by dcstar on 2010-10-25
> **vishuindian said:**
> Dear all
         I am trying to install ubuntu 10.04 on my laptop. But at installation time its unable to show my existing hard disk partition table instead its only show option to create new partition table. Although by running ubuntu 10.04 directly from cd , i can see following partition table on my disk.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77777777

   Device **Boot**      Start         End      Blocks   Id  System
**/dev/sda1   * **          1        1288    10344837    5 ** Extended**
/dev/sda2            1276        1288      104391   83  Linux
/dev/sda3            1289        3512    17864280   83  Linux
/dev/sda4            3513        9729    49938052+  83  Linux
/dev/sda5               1          13       96256   83  Linux
/dev/sda6              13         256     1951744   82  Linux swap / Solaris
/dev/sda7             256        1275     8188928   83  Linux
/dev/sda8            1275        1275        1406   83  Linux


Whats may be the reason? and how i can get my existing partition table at installation time.


The Boot partition should **not** be the Extended partition, that is only the container for actual partitions, set it to a "real" partition and see what happens.

---

### Post by srs5694 on 2010-10-25
> **vishuindian said:**
> Dear all
         I am trying to install ubuntu 10.04 on my laptop. But at installation time its unable to show my existing hard disk partition table instead its only show option to create new partition table. Although by running ubuntu 10.04 directly from cd , i can see following partition table on my disk.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1288    10344837    5  Extended
/dev/sda2            1276        1288      104391   83  Linux

In the future, please post columnar monospaced output, such as the output of "sudo fdisk -l", between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings; that will make it easier to read.

You've clearly got overlapping partitions. Note that your extended partition begins at cylinder 1 and ends at 1288, while /dev/sda2 (a primary partition that should *not* overlap with anything else) begins at 1276 and ends at 1288. My guess is that what is now /dev/sda2 began as a logical partition but somehow got converted into a primary partition by buggy partitioning software. If so, the solution is to convert it back; however, that could be tricky. It's possible there are other problems that aren't apparent from your output because fdisk has only displayed values in cylinders rather than the more precise sectors. There are several possible approaches to fixing this problem:


[list]
[*]Type "sudo sfdisk /dev/sda -d > parts.txt". You can then edit parts.txt, changing /dev/sda2 to /dev/sda9, and then type "sudo sfdisk /dev/sda < parts.txt" to rewrite the fixed partition table. Beware, though: There *must* be at least one unallocated sector prior to the altered partition, or it can't be converted into a logical partition. You'll need to figure out which partition comes before it and do the math to figure out if the required free space is available.
[*]Type "sudo fdisk -u /dev/sda" to launch fdisk interactively. Type "p" and note the exact start and end sector numbers for /dev/sda2. Note that you'll be working in *sectors,* not cylinders (as is the default). Type "d" to delete /dev/sda2, then type "n" to create a new partition. Tell it to create a logical partition and give it the exact start and end sector values used by the old /dev/sda2. Type "w" when you're done.
[*]Download the lastest version of my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program and launch it on the disk by typing "sudo gdisk /dev/sda". This will convert the disk to GUID Partition Table (GPT) form internally. Type "v" to have it verify the disk (check for errors and report on free space). If there's a free block of at least 35 KiB size, type "t" to create a new partition of type EF02, of between 35 KiB and 1 MiB in size. Type "w" to save the new partition table. This approach makes a rather radical change from MBR to GPT form, but it has the benefit of completely eliminating the annoying primary/extended/logical partition distinctions. Note that Windows can't boot from GPT unless you've got an EFI-based system; but it looks like this is a Linux-only disk, so it should be OK with GPT.
[*]Use GPT fdisk, as above, but once launched, type "r" to enter the recovery and transformation menu, then type "g" to convert the disk back to MBR format. You should be able to adjust which partitions become primary and which become logical, within the constraints of what configurations are legal. When you're satisfied with the layout, type "0" to accept it. Feel free to start this process, post a display of the partitions shown by typing "p" at the main menu and the initial suggested MBR layout, and then terminate it by pressing Ctrl+C. I'll then be able to advise you on good ways to proceed. (Note that I might not check back on the forum for a day or so, though.)
[/list]


It's possible you'll need to re-install GRUB in any of these cases, and particularly in the last two. Typing "sudo grub-install /dev/sda" should do that job. Alternatively, since you want to install the latest Ubuntu, you could just run the installer and let it install its version of GRUB.

---

### Post by srs5694 on 2010-10-25
> **dcstar said:**
> The Boot partition should **not** be the Extended partition, that is only the container for actual partitions, set it to a "real" partition and see what happens.

Although you're right that extended partitions shouldn't be marked as bootable/active, I don't believe this issue would account for the reported symptoms. (I just did a test and found no problems with GParted, at least.) The overlapping partitions, however, *do* cause this behavior in libparted-based tools, including GParted and the Ubuntu installer.

Removing the active/bootable flag from the extended partition is probably advisable, but this is secondary to fixing the overlapping partitions problem.

---

### Post by psusi on 2010-10-25
There has been a rash of people with partition tables corrupted in this way lately, I wonder what could be causing it?  What sort of partitioning tools have you been using?  You seem to have a number of existing Linux partitions.  Why is that?  What system(s) do you already have installed?

---

