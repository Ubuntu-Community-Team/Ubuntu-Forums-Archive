---
title: "Cloning to Advanced Format drive with 4096 bytes from 512 byte drive"
date: 2011-06-27
forum: General Help
---

### Post by 987a654 on 2011-06-27
I am getting a new 4kb sector HDD for my laptop, WD scorpio black 750gb, I would like to image existing partitions on 512bytes sector HDD and move them to the new 4kb sector HDD, what's the best way to do this.

present config is as follows:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c2997afa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux   		root partition Ubuntu
/dev/sda2        20964825    89176814    34105995   83  Linux		home partition
/dev/sda3   *    89176815   156296384    33559785    7  HPFS/NTFS	Win 7

I am planning to keep the same three partitions as the primary partitions on the new drive and add few more logical partitions. I would have liked to move to GPT but since I need Win 7, I am stuck with MBR partiotion table.

Now, I understand how to partition an Advanced format disk, what I want to know is how to move the existing partitions on the 80 Gb disk to the new disk? 

I use Clonezilla to copy partitions but it is not compatible unless both the target and the source disks are already using 4096 sector size. 

I can use  Acronis True Image WD Edition to clone Win 7 but how do  I clone Ubuntu?

Also my Laptop's chipset is limited to SATA 1.5, will it cause any issues, I know the bandwidth is not an issue. Any other gotchas

Yudi

---

### Post by srs5694 on 2011-06-27
> **987a654 said:**
> I am getting a new 4kb sector HDD for my laptop, WD scorpio black 750gb, I would like to image existing partitions on 512bytes sector HDD and move them to the new 4kb sector HDD, what's the best way to do this.

In the future, please use [noparse]```
[/noparse] and [noparse]
```[/noparse] tags around monospaced program output. That preserves column formatting which keeps the text legible. I'm adding it below, but sometimes it doesn't work properly in replies, so I can't guarantee it'll be an improvement....

> present config is as follows:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c2997afa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux           root partition Ubuntu
/dev/sda2        20964825    89176814    34105995   83  Linux        home partition
/dev/sda3   *    89176815   156296384    33559785    7  HPFS/NTFS    Win 7
```

All three of your partitions begin on odd-numbered sectors, so they clearly aren't properly aligned for your new drive. This makes a direct dd copy a poor choice.

> I am planning to keep the same three partitions as the primary partitions on the new drive and add few more logical partitions. I would have liked to move to GPT but since I need Win 7, I am stuck with MBR partiotion table.

If you're up for an adventure, you could use [UEFI DUET](http://www.rodsbooks.com/bios2uefi/) and [this procedure](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI) to get Windows booting using UEFI DUET. (FWIW, when I did this on my laptop I didn't need to deal with the Registry editing, which simplified matters.) In fact, since you're cloning your installation, that's a good time to do it; you can clone the drive to GPT, install the UEFI DUET software, and if it doesn't work, [wipe the GPT data](http://www.rodsbooks.com/gdisk/wipegpt.html) and start over again, with no risk to your data (aside from the usual risks when dealing with disk duplication operations). OTOH, this is definitely a "bleeding-edge" type of setup, so if you're less than highly technically inclined, I don't advise trying it. I only suggest it as a possibility because your level of awareness of the problems involved in swapping your disks suggests you might have the necessary prerequisite skills.

FWIW, one advantage of switching to UEFI DUET booting of Windows is that Windows is much less sensitive to partition start point issues under UEFI than it is under BIOS. In a test, I successfully moved a bootable Windows partition from one point on a disk to another (with no overlap at all between the two locations) using GParted and Windows booted just fine at its new location, with no adjustments required at all.

> Now, I understand how to partition an Advanced format disk, what I want to know is how to move the existing partitions on the 80 Gb disk to the new disk? 

I use Clonezilla to copy partitions but it is not compatible unless both the target and the source disks are already using 4096 sector size. 

I can use  Acronis True Image WD Edition to clone Win 7 but how do  I clone Ubuntu?

I'm only passingly familiar with Clonezilla and not at all with Acronis, so I can't comment on how to use them for the job. I have used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) to move a Windows 7 installation from one point on a disk to another, and any tool you use will have to be able to do the same. Under BIOS, Windows is very sensitive to its partition start points, so you can't use Linux's ntfsclone to do the job, since it doesn't make the necessary adjustments. You *could* use ntfsclone to clone from your current disk to a GPT disk if you intended to go the UEFI DUET route, though. (At least, assuming you don't need Registry adjustments after cloning.)

In this sort of situation, I generally copy Linux installations by:


[list=1]
[*]Creating suitable partition(s) on the target disk.
[*]Creating suitable filesystem(s) on the target partition(s).
[*]Mounting the original partition(s) and the new partition(s) using an emergency boot disc. I'll suppose the original is at /source and the destination is at /dest.
[*]Using tar to copy from one to the other, as in "cd /source; tar cf - . | (cd /dest; tar xvf -)".
[*]Adjusting UUID references in the /etc/fstab file and boot loader configuration file on the destination.
[*]Installing the boot loader on the destination.
[/list]


Alternatively, if the source and destination drives can't be connected simultaneously (as might be the case for a laptop drive swap), creating a backup tarball on a network server or external backup disk as an intermediary works fine, albeit a bit more slowly since two copies are required rather than two.

Clonezilla is probably a slightly simpler way to do things, but I've been doing it the way I describe for quite a while, so I understand it pretty well. It also gives the opportunity to do things like change the filesystem used on the source and destination, change partition layout (say, if you wanted to split off /usr into its own partition), swtich to an LVM configuration, etc. Some of these would require building a new initial RAM disk, though.

If you were to combine this with a GPT conversion, it'd be best to create a BIOS Boot Partition before installing GRUB on the destination disk. Alternatively, you could boot Linux via UEFI DUET, but then you'd need to install a UEFI boot loader for Linux, which would be more work. IMHO, such a setup works best with GRUB 2 as the MBR-resident BIOS boot loader, BootDuet installed to either the EFI System Partition (ESP) or its own dedicated partition, GRUB 2 configured to choose between Linux and BootDuet, and Windows set up as the default boot option in UEFI DUET.

---

### Post by 987a654 on 2011-06-29
Thanks for your quick and detailed reply.

I did not know about UEFI DUET, interesting option but I will not be going that way. It looks like lot of time wasting. 

Usage looks similar to plop boot manager, I use plop on really old systems to boot from USB. 

Well, I was interested in GPT because it treats all partitions as same, no more primary and logical ones.Thats my major gripe. 

I will probably go with clean installs and move my data later. At least with Ubuntu, thats looks like the only option. I am pressed for time otherwise I would like to play around with cloning. I am not sure what sort of performance I can expect from a cloned sys vis-a-vis clean install.

I gathered the following info from WD's website, they recommend kernel 2.6.34. 

> The Linux kernel has had specific support for the alternate sector sizes and offsets used by WD Advanced Format disk drives since version 2.6.31. However, distributions based on Linux 2.6.34, the latest stable version of Linux, will provide the most thorough support. Advanced Format parameters are available in the sysfs file system from this kernel version onwards.

I need to find out which distribution comes with this kernel out of the box.

will post back once I complete the setup.

Yudi

---

### Post by srs5694 on 2011-06-29
Concerning Linux kernel versions, don't worry about it. Although it's true that system calls for determining logical vs. physical sector size exist in recent kernels, every Advanced Format drive I've used (two WDs and one Seagate) has given inaccurate information on that score, so those system calls are 100% useless when applied to these drives. WD's recommendation that you use such a drive is therefore pretty pointless. (FWIW, WD has a history of making pointless or misleading claims about Linux. I wouldn't trust anything they said on the topic.)

That said, recent distributions have long moved beyond kernel 2.6.31. Ubuntu 11.04 is based on 2.6.38, IIRC.

---

### Post by 987a654 on 2011-08-19
Hi srs5694,

hard disk setup:

sda1 - win7
sda2 - /boot
sda3 - LVM on top of LUKS partition - (separate LVs for /, /home, and SWAP)
sda5 - FAT32

below you will see fdisk output. Does it really matter if sda4 does not start on a physical sector boundary. It's an extended partition. sda5 starts on the sector boundary. Every partition start sector is divisible by 8 except sda4. 

Not sure how I missed it. Apart from sda4 is everything fine?


```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00002307

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104859647    52428800    7  HPFS/NTFS
/dev/sda2       104859648   106956799     1048576   83  Linux
/dev/sda3       106956800  1155532799   524288000   83  Linux
/dev/sda4      1155534846  1465149167   154807161    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1155534848  1465149167   154807160    7  HPFS/NTFS

Disk /dev/dm-0: 536.9 GB, 536869859328 bytes
255 heads, 63 sectors/track, 65270 cylinders, total 1048573944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 20.5 GB, 20476592128 bytes
255 heads, 63 sectors/track, 2489 cylinders, total 39993344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 51.2 GB, 51199868928 bytes
255 heads, 63 sectors/track, 6224 cylinders, total 99999744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 4093 MB, 4093640704 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table


```

---

### Post by srs5694 on 2011-08-19
> **987a654 said:**
> below you will see fdisk output. Does it really matter if sda4 does not start on a physical sector boundary. It's an extended partition. sda5 starts on the sector boundary. Every partition start sector is divisible by 8 except sda4. 

Not sure how I missed it. Apart from sda4 is everything fine?

Don't worry about the alignment of extended partitions. Alignment is an issue because most filesystems store data in collections of 4 KiB blocks If those blocks aren't aligned with the underlying sectors on Advanced Format drives, the result is extra reads from and, especially, writes to sectors. That is, to write one of these 4 KiB data structures, the drive needs to read two sectors, modify parts of both of them, and then write both back. If the partition is aligned, the drive can just write the 4 KiB data structure directly, which is faster.

In the case of an extended partition, there are just a few sectors of data that belong to it, and they're scattered about. They are the Extended Boot Records (EBRs), which define where logical partitions begin and end. EBRs are seldom written, and they're less than 4 KiB in size, so you'll always get the performance penalty when writing them, but it will be unimportant.

Logical partitions, of course, must be aligned; like primary partitions, they're just a way to define where the filesystems they contain begin and end. As in your case, though, logical partitions can be aligned differently from the extended partitions that contain them.

---

### Post by 987a654 on 2011-08-20
> **srs5694 said:**
> Don't worry about the alignment of extended partitions. 

In the case of an extended partition, there are just a few sectors of data that belong to it, and they're scattered about. They are the Extended Boot Records (EBRs), which define where logical partitions begin and end. EBRs are seldom written, and they're less than 4 KiB in size, so you'll always get the performance penalty when writing them, but it will be unimportant.



I thought so too, thanks for clarifying.
> 
Logical partitions, of course, must be aligned; like primary partitions, they're just a way to define where the filesystems they contain begin and end. As in your case, though, logical partitions can be aligned differently from the extended partitions that contain them.


well, I got nothing on sda5 so I will redo the extended partition.
so far I have not noticed any performance issues. Drive works just fine.

Thanks once again for all your help.

---

### Post by srs5694 on 2011-08-20
> **987a654 said:**
> well, I got nothing on sda5 so I will redo the extended partition.
so far I have not noticed any performance issues. Drive works just fine.

Your /dev/sda5 is properly aligned, so there's no point in redoing the extended partition, except perhaps to eliminate the unnecessary warning about the extended partition being improperly aligned.

---

