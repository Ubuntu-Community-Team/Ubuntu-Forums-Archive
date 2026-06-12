---
title: "help with ext3 partition"
date: 2010-04-24
forum: General Help
---

### Post by rebeltaz on 2010-04-24
I had a 500gb hard drive that I wanted to use on my Ubuntu system as a media storage drive. The drive originally had two partitions on it, one was a Dell Recovery partition and the other was a Windows Vista partition. Using the Palimpsest Drive Utility that comes with Ubuntu, I deleted both partitions, created a Ext3 partition using 100% of the space and copied my data to the drive. After I finally got fstab to load the drive, I found another problem. 

First of all, when Grub loads, two options it offers are:

Windows Vista (loader) on sdc1
Windows Vista (loader) on sdc3

Aside from that, 100% of the drive is not being used by the Ext3 partition. It is showing 434.6gb available on the drive. Fdisk is not showing any other partitions on this drive, so A) why are the Windows loader options showing up under Grub and B) why do I not have 500gb available?

Here is a copy of the output fdisk -l:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04f8ce84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 80.0 GB, 80024264704 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           4       32098+  de  Dell Utility
/dev/sdd2   *           5        9729    78116062+   7  HPFS/NTFS
```

Thanks...

---

### Post by Yogotiss on 2010-04-24
sounds like what you may want to do is a low level format or when installing a fresh copy of ubuntu select the option to "use entire disk".

how long ago did you install this copy of ubuntu?

---

### Post by Kljuka on 2010-04-24
This might also be the difference betwen Gigabytes and Gibibytes.

You can manually delete entries from grub (/boot/grub/menu.lst), but be careful not to delete wrong entries or you won't be able to boot.

---

### Post by rebeltaz on 2010-04-24
> **Yogotiss said:**
> sounds like what you may want to do is a low level format or when installing a fresh copy of ubuntu select the option to "use entire disk".

how long ago did you install this copy of ubuntu?

I installed Ubuntu on this system when 9.10 came out, but Ubuntu isn't in the drive I'm having trouble with. This is just going to be a storage drive...

How do I do a low-level format under Ubuntu?

> **Kljuka said:**
> This might also be the difference betwen Gigabytes and Gibibytes.

You can manually delete entries from grub (/boot/grub/menu.lst), but be careful not to delete wrong entries or you won't be able to boot.

I don't mind the grub entries, I was just concerned that the entries indicated that the entire drive wasn't being used.

---

### Post by srs5694 on 2010-04-24
First, it's impossible to do a low-level format on most (maybe all) modern hard disks. You can low-level format floppies using fdformat, but not hard disks. The advice to perform a low-level format to fix smaller-than-expected disk size is misinformation that's been floating around since the mid-1990s, if not longer.

Second, the size difference you're seeing is almost certainly a result of several factors:


[list]
[*]As Kljuka suggests, part of the difference is that between gigabytes (GB) and gibibytes (GiB; what most utilities and people mean when they use the "GB" abbreviation). Your disk has 500,107,862,016 bytes, which is 500.1GB (being technically correct with abbreviations, which drive manufacturers are) but just 465.8GiB.
[*]Depending on how you're determining your "434.6gb" figure, much of the remaining difference is probably due to the 5% that ext2/3/4fs sets aside for use by root. 5% of 465.8GiB is 23.3GiB, bringing the expected available space figure down to 442.5GiB.
[*]The remaining 7.9GiB difference is probably attributable to the journal, which is pre-allocated in ext2/3/4fs.
[/list]


You can reduce the amount of space reserved for root by using the -m option to tune2fs:

```

sudo tune2fs -m 0 /dev/sdc1

```

A 0% reserved blocks percentage is probably reasonable for your stated use. Normally reserving space is only desirable on the main system partition(s), such as root (/) and, if they're present, perhaps /var, /usr, or some others.

Incidentally, if your media are large files (larger than a few hundred MiB), you may want to use JFS, XFS, or perhaps ext4fs rather than ext3fs. Although ext3fs is a popular filesystem, it doesn't handle large files all that well. JFS, XFS, and ext4fs all handle such files better. (They're faster, particularly with operations like deletions.) IMHO, XFS is the most reliable of these filesystems at the moment, so it's what I recommend.

Finally, Kljuka's suggestion of manually editing /boot/grub/menu.lst will work if you're using the older GRUB Legacy, which was standard through Ubuntu 9.04, IIRC. Since then, Ubuntu has switched to the newer GRUB 2, which uses /boot/grub/grub.cfg, although this file is auto-generated; files in /etc/grub.d ultimately control what goes in /boot/grub/grub.cfg. The grub-mkconfig command should theoretically auto-detect what OSes you've got on your system and generate a new configuration file.

---

### Post by rebeltaz on 2010-04-24
> **srs5694 said:**
> Second, the size difference you're seeing is almost certainly a result of several factors:


[list]
[*]As Kljuka suggests, part of the difference is that between gigabytes (GB) and gibibytes (GiB; what most utilities and people mean when they use the "GB" abbreviation). Your disk has 500,107,862,016 bytes, which is 500.1GB (being technically correct with abbreviations, which drive manufacturers are) but just 465.8GiB.
[*]Depending on how you're determining your "434.6gb" figure, much of the remaining difference is probably due to the 5% that ext2/3/4fs sets aside for use by root. 5% of 465.8GiB is 23.3GiB, bringing the expected available space figure down to 442.5GiB.
[*]The remaining 7.9GiB difference is probably attributable to the journal, which is pre-allocated in ext2/3/4fs.
[/list]

...

Incidentally, if your media are large files (larger than a few hundred MiB), you may want to use JFS, XFS, or perhaps ext4fs rather than ext3fs. Although ext3fs is a popular filesystem, it doesn't handle large files all that well. JFS, XFS, and ext4fs all handle such files better. (They're faster, particularly with operations like deletions.) IMHO, XFS is the most reliable of these filesystems at the moment, so it's what I recommend.


OK.. so the amount of space is probably correct?

The reason I finally decided on ext3 was because of what I read about risk. Unless I was misinformed, the other filesystems, XFS and ext4 especially, do not right immediately to the disk, risking data loss if a power outage occurs before the files have a chance to be written. Is that still true? Is there a way to convert to XFS from ext3 if I were to decide to go that route? I do use that drive to store 4.7gb DVD ISO images routinely.

---

