---
title: "Change Drives, Move Filesystem"
date: 2009-07-23
forum: General Help
---

### Post by redwaldmcmanus on 2009-07-23
Hi all.

I'm looking to move my hard disks around, and my mount points.

Currently:

sda is mounted at /
sdb id mounted at /home (and also has the swap partition)

and sdc is bigger than them both combined.

I keep on my music and videos on an external hard disk (sdd), so space in the home directory is a major concern, I just mounted a different drive cos I thought there would be a slightly faster load speed.

Ideally, I think I want sdc to be the filesystem and keep sdb at /home.


How would I go about moving my things over and then sorting GRUB and fstab out?

Any advice welcomed, cheers.

---

### Post by ajgreeny on 2009-07-23
I'm sure all of this is possible, but I honestly think it would be easier and much quicker to start again and reinstall with everything where you want it.  If you try to do it by moving everything as you suggest, I think it will be a long job, cloning and backing up the partitions and will take probably a lot longer than a quick rsync to back up everything you need to your external drive, reinstall, and then copy everything back again.

See what others think first, but that's what I would do.

---

### Post by redwaldmcmanus on 2009-07-23
yeah, that was my thoughts.

I thought I'd try installing 64bit on the new disk and that way I've got 32bit on the old disk to fall back on if any probs.

Thanks though

---

