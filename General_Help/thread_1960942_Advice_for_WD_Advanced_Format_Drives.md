---
title: "Advice for WD Advanced Format Drives"
date: 2012-04-18
forum: General Help
---

### Post by growingneeds on 2012-04-18
Hi,

I have a Western Digital Advanced Format drive. With a new installation of Lucid, it showed a disk alignment warning. The misalignment occurs in the extended partition that houses the swap partition. I have used Lucid for almost 2 years, and now am moving on to Oneiric. However, upon a new installation, the same problem occurs. The screen capture for Disk Utility (Oneiric) as shown

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216225&d=1334755021[/IMG]

The output from the terminal command "sudo fdisk -lu" shows
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00031d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   974694399   487346176   83  Linux
/dev/sda2       974696446   976771071     1037313    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       974696448   976771071     1037312   82  Linux swap / Solaris
```

Other forum members seem to have a similar problem. These are the new AF drives. Something about a 4096 byte sector instead 512. Something about older machines not being able to boot due to BIOS incompatibility. Many have suggested re-aligning with tools from WD, but it requires installing Windows, and possibly keeping it that way.

As it is, I am currently writing this post from within Oneiric. It functions well. But it bugs me that there is a misalignment issue that might interfere my next Suspend / Hibernate attempt. Short of installing Windows, is there a solution to AF drive's misalignment issues?

Thank you for reading my lengthy rant.

---

### Post by dino99 on 2012-04-18
[http://askubuntu.com/questions/103855/partition-is-misaligned-by-3072-bytes-pavilion-dv7-6199us](http://askubuntu.com/questions/103855/partition-is-misaligned-by-3072-bytes-pavilion-dv7-6199us)

---

### Post by oldfred on 2012-04-19
Some more info. But the extended partition is just a container for logical. The alignment really needs to be on partitions you write into, and you do not write into the extended partition. So if the logicals are aligned you are ok.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for other Debian installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignement issue.

The articles that Olfred provides are great. The link to askubuntu.com is informative. But the advice given in those places aren't practical. These days, I feel quite alienated from Ubuntu. Developers don't speak to the layman; and the layman, developers.In any case, using GPartEd Live to partition the HDD to nearest MB solves the problem. I usually choose the "Unformatted" option for these drives.

Hope this helps.

---

### Post by techsupport on 2012-04-23
> **growingneeds said:**
> The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for other Debian installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignement issue.

The articles that Olfred provides are great. The link to askubuntu.com is informative. But the advice given in those places aren't practical. These days, I feel quite alienated from Ubuntu. Developers don't speak to the layman; and the layman, developers.In any case, using GPartEd Live to partition the HDD to nearest MB solves the problem. I usually choose the "Unformatted" option for these drives.

Hope this helps.

You are right. I use Gparted and wipe everything with that first, before I install Ubuntu on a unfamiliar hard drive.  New partition table, partitions, the works. ):P

---

