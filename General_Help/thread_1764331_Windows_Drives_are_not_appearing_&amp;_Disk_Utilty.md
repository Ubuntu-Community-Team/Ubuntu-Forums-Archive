---
title: "Windows Drives are not appearing &amp; Disk Utilty shows Spaces above the capcity of HD."
date: 2011-05-21
forum: General Help
---

### Post by naikaniket.23 on 2011-05-21
I had installed Ubuntu 10.04 on dual boot mode with Windows 7, I had to migrate from windows 7 to XP & again to windows 7. Each time after installation I updated grub. Last time while updating Grub PC went Down due to power failure. I update grub after the supply was resumed and it was successful. 

On login I am facing a weird problem, My windows Drive are not appearing in Ubuntu. To access the drives I have to Plug a Pen Drive and access them first from an Application otherwise the don't even appear in Places drop-down list. If I don't plug Pen Drive they don't appear in Applications.

The other problem is that Disk utility shows space unallocated, allocated & Free above the physical capacity of Hard disk. My Hard disk is of 160 GB, Disk utility Shows Unallocated Space 18446744 TB. The Default Partitions made by me are 26GB, 14GB & others of 40 GB each.


Please help me to solve this Problems. Thanks in advance.

---

### Post by linuxinstalledfromhdd on 2011-05-21
Sounds like it would be a good time to repartition the entire disk and reformat everything. Esp if you are getting size errors reported.. That's not good at all.

---

### Post by srs5694 on 2011-05-21
Please run the following command in a Terminal window:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will show us what you're up against, more precisely and accurately than Disk Utility does. (Note that this use of fdisk is *not* intended to fix anything; it just shows the partition table.)

---

### Post by dcstar on 2011-05-23
> **naikaniket.23 said:**
> 
.........
Please help me to solve this Problems. Thanks in advance.

Any disk that has SMART telling you that it has bad blocks should be replaced.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I totally second that opinion. If you run Disk Check and it gives you anything less than a "good" signal, it's time for the trash can with that bad boy.):P

---

### Post by naikaniket.23 on 2011-05-24
> **srs5694 said:**
> Please run the following command in a Terminal window:

```

sudo fdisk -lu

```Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will show us what you're up against, more precisely and accurately than Disk Utility does. (Note that this use of fdisk is *not* intended to fix anything; it just shows the partition table.)
Hi [srs5694]("http://ubuntuforums.org/member.php?u=1032238"),
As you required following is the result for the command: -

"omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd764d764

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51439245    25719591+   7  HPFS/NTFS
/dev/sda2        51441662   312560639   130559489    f  W95 Ext'd (LBA)
/dev/sda3        78140223   156280319    39070048+   7  HPFS/NTFS
/dev/sda5        51441664    78139391    13348864   83  Linux
/dev/sda6       156280383   234420479    39070048+   7  HPFS/NTFS
/dev/sda7       234420543   312560639    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 2019 MB, 2019557376 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4   *          63     3944447     1972192+   6  FAT16
Partition 4 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 135, 18 )  "

Please help me. Thanks in advance.

---

### Post by srs5694 on 2011-05-24
> **naikaniket.23 said:**
> Hi [srs5694]("http://ubuntuforums.org/member.php?u=1032238"),
As you required following is the result for the command: -

It would have been easier if you'd also included the [noparse]```
[/noparse] and [noparse]
```[/noparse] formatting I specified. I'm adding that below, but this detail sometimes doesn't work properly when added in quoted text....

> ```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd764d764

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51439245    25719591+   7  HPFS/NTFS
/dev/sda2        51441662   312560639   130559489    f  W95 Ext'd (LBA)
/dev/sda3        78140223   156280319    39070048+   7  HPFS/NTFS
/dev/sda5        51441664    78139391    13348864   83  Linux
/dev/sda6       156280383   234420479    39070048+   7  HPFS/NTFS
/dev/sda7       234420543   312560639    39070048+   7  HPFS/NTFS
```

Please help me. Thanks in advance.

Your /dev/sda3 is a primary partition, but it's located in the middle of an extended partition. This is illegal and is confusing libparted, upon which Disk Utility is based.

The easiest solution is to run my [FixParts](http://www.rodsbooks.com/gdisk/fixparts/) program, which can automatically correct this sort of problem. Read its Web page for details. Note that this fix will change the partition numbers of some of your partitions. With recent Ubuntu installations, this won't cause problems unless you've manually edited /etc/fstab or your GRUB configuration; however, if you've done so, you may need to make changes to those files before your computer will boot again.

---

### Post by naikaniket.23 on 2011-05-26
Hi [srs5694]("http://ubuntuforums.org/member.php?u=1032238"),

I used FixParts program it fixed the problem of the non appearing drives & Disk utility program errors. Thanks.
I noticed that the Disk Utility now does not shows the Partition but on executing the command '

sudo fdisk -lu


The Results is as below

$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd764d764

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *                 63    51439245    25719591+   7  HPFS/NTFS
/dev/sda2       234420543   312560639    39070048+   7  HPFS/NTFS
/dev/sda3         51441663   156280319    52419328+   f  W95 Ext'd (LBA)
/dev/sda4       156280383   234420479    39070048+   7  HPFS/NTFS
/dev/sda5         51441664    78139391    13348864   83  Linux
/dev/sda6         78140223   156280319    39070048+   7  HPFS/NTFS

Partition table entries are not in disk order
The extended drive is still appearing here is it harmful ?

---

