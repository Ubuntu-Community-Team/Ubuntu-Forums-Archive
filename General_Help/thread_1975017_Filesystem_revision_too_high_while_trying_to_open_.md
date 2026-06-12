---
title: "Filesystem revision too high while trying to open ..."
date: 2012-05-06
forum: General Help
---

### Post by deserttrail on 2012-05-06
Hi all,

I'm running 10.04 and I have a RAID5 (mdadm) array using LVM on top of that with four logical volumes.  During a reboot, one of the partitions failed its check and wanted to be fixed manually:

```

# e2fsck /dev/vgRaid/mythtv
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Filesystem revision too high while trying to open /dev/vgRaid/mythtv
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)

The superblock could not be read or does not desribe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

It's an ext4 partition and I've tried using the suggested command, plus a few other backup-superblock guesses given by "mke2fs -n <device>" with no luck.

```

# e2fsck -b 32768 /dev/vgRaid/mythtv
...
e2fsck: Bad magic number is super-block while trying to open /dev/vgRaid/mythtv
...

```

I'm not sure what the blocksize is for the partition so I tried a few from each of "mke2fs -b 1024 -n <device>", "mke2fs -b 2048 -n <device>", and "mke2fs -b 4096 -n <device>" all with the same result.

The other partions on the volume groups seem to have mounted just fine so I don't *think* the array or lvm are the problems.

Any ideas, either to recover the partition or the files?

Thanks

Edit - Additional info:

Found a backup superblock that worked - kinda:

```

# e2fsck -b 1605632 /dev/mapper/vgRaid-mythtv
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 131072000 blocks
The physical size of the device is 104857600 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>?

```

Not sure what to do with that.

---

