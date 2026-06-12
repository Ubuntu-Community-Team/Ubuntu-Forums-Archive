---
title: "Mirror Backup"
date: 2010-12-26
forum: General Help
---

### Post by quequotion on 2010-12-26
I'd like to make a mirror back up of my entire filesystem (2TB) on to a USB drive (2TB). It needs to have every symlink, every system file, etc  with all their original permissions and properties in order to be bootable in case something goes wrong. I even partitioned the drive to match the original, but it lacks it's own GRUB.

I don't think I can make a RAID:1, since the filesystem is already a fakeRAID:0, and I'd rather not anyway. I want a backup that's slightly behind the latest changes (an hour, a login, or a day).

There are a lot of tools out there for this sort of thing. I like backintime and rsync because they can save time by skipping unchanged data, but I don't know what options to use to make a perfect mirror.

---

### Post by Ceiber Boy on 2010-12-26
> **quequotion said:**
> I'd like to make a mirror back up of my entire filesystem (2TB) on to a USB drive (2TB). It needs to have every symlink, every system file, etc  with all their original permissions and properties in order to be bootable in case something goes wrong. I even partitioned the drive to match the original, but it lacks it's own GRUB.

I don't think I can make a RAID:1, since the filesystem is already a fakeRAID:0, and I'd rather not anyway. I want a backup that's slightly behind the latest changes (an hour, a login, or a day).

There are a lot of tools out there for this sort of thing. I like backintime and rsync because they can save time by skipping unchanged data, but I don't know what options to use to make a perfect mirror.

I think RAID 1 is going to be the best answer! Even if it is not exactly what you want.

---

### Post by quequotion on 2010-12-30
> **Ceiber Boy said:**
> I think RAID 1 is going to be the best answer! Even if it is not exactly what you want.

I have some good reasons to not want it. In case something bad happens to the filesystem, like corruption or accidental deletion of data, I don't want to sync that to the backup. Also, the bandwith difference of the two drives makes this impractical if not impossible. (RAID:0 on SATA2x4 vs HDD on USB2.0)

It would be better to have a backup that is periodically synced and avoids the very latest changes, even if it means losing the last (few) hour(s).

As for syncing files for backup, rsync seems like it has the ability to do most of what I want, but I don't know the syntax well enough.

Is there any way to sync GRUB across (non-RAID) disks?

Perhaps this isn't as complicated as I think?

---

### Post by quequotion on 2010-12-30
Some specs:

2TB RAID:0 (4x 500GB SATA2):
2 Partitions, linux swap and ext4 (at /)
Average Read Rate: 254.0 MB/s (theoretically this should be much higher...)
Average Access Time: 18.6ms (theoretically this should be much faster...)

2TB USB (1x 2TB SATA2 on USB)
2 Partitions, linux swap and ext4 (at /media/backup)
Average Read Rate: 34.5 MB/s
Average Access Time: 14.6 ms

Best-case-senario, without creating some kind of magic caching protocol, I could make a RAID:1 with a 34.5 MB/s read rate and 18.6 ms access time. If it worked at all, it would be excruciatingly slow.

An asynchronous backup would do a better job.

---

### Post by quequotion on 2010-12-30
My plan so far:

Use BackInTime (root) to make an hourly backup of /

If anything ever goes wrong,

1. reboot with a livecd

2. mount backup drive

3. move latest backup to the root of the drive

4. chroot in

5. install/update grub in the chroot

6. reboot

This might work, but I'll still have in inoperable system for a while.

It would be better if I could:

A. backup "/" directly to "/media/backup/" (BackInTime will embed the backup two folders deep, /backitime/date-and-time/)
--rsync can probably do that but I don't know how to use it that well...
--anyone see any caveats in:```
rsync --recursive --times --perms --links --delete / /media/backup/
```

B. sync grub between two non-RAID drives. 
--can anything do that?

---

