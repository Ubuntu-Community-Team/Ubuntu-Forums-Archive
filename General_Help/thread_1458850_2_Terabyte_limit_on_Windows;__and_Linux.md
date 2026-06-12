---
title: "2 Terabyte limit on Windows;  and Linux?"
date: 2010-04-20
forum: General Help
---

### Post by egalvan on 2010-04-20
I know that most Windows OS's have a 2 Terabyte Hard drive limit...
It's been making the rounds on forums and in print.

Now the Chcken-Little sites state it as a universal limit:
"limit to hard drive space reached... new software needed!"

But the good reviews always mention Windows by name.
"32-bit Microsoft OS cannot handle drives larger than 2 Terabytes,
you will need to upgrade to 64bit Microsoft OS"


Does this 2 Terabyte Hard drive limit hold for Linux?

---

### Post by Chronon on 2010-04-20
Such limits depend on the file system being used.
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by 98cwitr on 2010-04-20
For Windows, you have to use GUID instead of MBR on the drives

[http://carltonbale.com/how-to-break-the-2tb-2-terabyte-file-system-limit](http://carltonbale.com/how-to-break-the-2tb-2-terabyte-file-system-limit)

---

### Post by LowSky on 2010-04-20
I thought this was a windows XP issue... and it isn't the first time the OS had a hard drive space issue.

Stop trying to use a 9 year old OS. Move on to Win7 or another newer OS

---

### Post by srs5694 on 2010-04-21
Chronon and 98cwitr both have part of the answer.

The most important 2TiB limit at the moment is built into the Master Boot Record (MBR) partitioning system, which uses 32-bit sector pointers to define the starts and lengths of partitions. Combined with the near-universal 512-byte sector size, this results in a size limit of (2^32 * 512) = 2,199,023,255,550 bytes (2TiB precisely). This limit applies to *any* OS that uses MBR; however, the limit can be lifted a bit by using larger sector sizes. Currently, no hard disks do this, although I believe some RAID controllers enable a translation scheme to present larger logical sector sizes. (Some very recent Western Digital drives use 4096-byte sectors, but they use in-firmware translation to present 512-byte sectors to the computer, so they don't help.)

The filesystem issue is also important, but as the link that Chronon presents indicates, most modern filesystems have limits that are at least somewhat beyond the 2TiB limit. (According to that Wikipedia article, it's 8TiB for FAT32, 16EiB for NTFS, 32TiB for ext2/ext3, 1EiB for ext4, 8EiB for XFS, etc.)

As a practical matter, if you've got a >2TiB RAID array, you should look into the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) as a replacement for the old MBR partitioning system. Linux fully supports GPT. Contrary to what some people claim, GPT works fine on BIOS-based systems, at least for Linux. (Windows can't boot from GPT disks on BIOS-based computers, but that's a Windows limitation. Linux boots fine from GPT disks on BIOS-based computers.) In fact, even on smaller disks, GPT has some minor advantages, such as the removal of the awkward primary/extended/logical partition distinction, partition names, an on-disk backup of the partition data for improved security, and CRC checksums of partition data to help detect corruption of the partition table. I therefore recommend that GPT be used on Linux-only installations, particularly if you want to understand GPT prior to its being forced on you when you buy your first >2TiB disk.

---

