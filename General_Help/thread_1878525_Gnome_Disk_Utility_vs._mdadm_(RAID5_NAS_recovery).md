---
title: "Gnome Disk Utility vs. mdadm (RAID5 NAS recovery)"
date: 2011-11-09
forum: General Help
---

### Post by redgar99 on 2011-11-09
Howdy, long time reader, first time poster.  Been googling furiously the last three nights trying to recover a three disk RAID5 from a bad NAS box (Promise NS4600).  Lots of solutions out there but can't find one quite like mine.

I have the three drives attached and Gnome Disk Utility says they each have a 500GB "Raid Component".  However mdadm refuses to play along mostly because there is no md superblock detected (pasted below).  My next step is to see if it makes sense to try to just create the new md raid as I've seen some folks do, with some chance of losing my data.  I'm wondering if I should I let DU try to create the raid at the Gnome level, assuming it will know what to do with these existing components.  **Or to step back, what is it that makes DU think these are parts of a RAID, but yet keeps mdadm from putting any of the pieces together.**

[INDENT]sudo mdadm --examine /dev/sd[acd]
mdadm: No md superblock detected on /dev/sda.
mdadm: No md superblock detected on /dev/sdc.
mdadm: No md superblock detected on /dev/sdd.[/INDENT]

or...

[INDENT]sudo mdadm --assemble --force /dev/md0 /dev/sd[acd]mdadm: no recogniseable superblock on /dev/sda
mdadm: /dev/sda has no superblock - assembly aborted[/INDENT]

---

### Post by redgar99 on 2011-11-11
Here is my fdisk -l output on one of the formerly RAID drives:

[INDENT]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table[/INDENT]

If I change the partition to fd (Linux RAID auto), will that kill any chances of ever recovering the data? Or even get me to a point where mdadm could reassemble the RAID?

Plain fdisk gives me the ominous message below:
[INDENT]Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x444985fa.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

[/INDENT]

TIA

---

