---
title: "linux raid partition vs. linux basic data partition"
date: 2011-04-27
forum: General Help
---

### Post by AllGamer on 2011-04-27
so i Googled around, read what was on the Wikipedia [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

but i still don't quite get what are the benefits of the RAID partition type vs basic data partition type

linux raid partition vs. linux basic data partition

i can set either type indifferently on my RAID5, and i can't yet figure out what one type does that the other one doesn't do.

if anyone knows more or have links to additional information sources it'll be much appreciated.


my volumes are formatted as EXT3, so the "benefit" of the basic data partition is not applicable since windows can not read it, even if it has the same GUID for the RAID5 partition

---

### Post by srs5694 on 2011-04-27
The GPT "basic data" partition type is intended to hold filesystem data -- FAT, NTFS, ext2/3/4fs, XFS, etc. (Unfortunately, Windows and Linux share the same type code in GPT, which is confusing.)

The RAID partition type is used to identify partitions that will be combined into a RAID array using Linux's RAID tools. Ultimately, filesystem data are likely to be stored on such volumes, but the data may be split up, merged together, or otherwise interpreted by the RAID subsystem.

You say you're using RAID5, but it's not clear to me if you're using hardware RAID, motherboard-based software RAID (aka "fake RAID"), or Linux software RAID. This detail is critical, and in the last case, it's important where your GPT data reside -- on the raw underlying disks (/dev/sda, /dev/sdb, etc.) or on a combined RAID device (/dev/md0 or similar). You'd only use the RAID partition type when using Linux's variety of software RAID, and then only on the underlying physical disks. In all other cases, you should use the "basic data" type for most Linux filesystems.

Also, if you use a libparted-based tool (GNU Parted, GParted, etc.), they don't report partition types at all; they set the type appropriately based on the filesystem you use on a device. In some cases, such as for RAID devices, you set the type code by setting a "flag" (called "raid", appropriately enough, for RAID partitions). If you use gdisk to partition your disk, you set the partition type via a 4-digit hexadecimal number -- 0700 for Linux/Windows data partitions or FD00 for Linux RAID partitions, among other possibilities.

---

### Post by AllGamer on 2011-04-27
Thank you very much, that is very informative.

I'm running several "fakeRAID" (cheap hardware RAID, using manufacturer provided drivers+Management software) RAID5 in my system, and i just wanted to make sure I've set the proper type of partitions for them.

but from your information, it seems like it's fine to leave it as basic data partition.

i sort of had a hunch, the raid partition type would most likely be used by softRAID such as mdadm, but when i created a RAID5 using mdadm and it didn't offer me the option to choose the partition type for the volume, it made me think back and left me wonder about the difference of those 2 types of partitions.

---

