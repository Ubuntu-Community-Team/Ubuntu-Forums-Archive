---
title: "fsck /boot [563] terminated with status 1"
date: 2011-10-16
forum: General Help
---

### Post by tehtide on 2011-10-16
Ok... I upgraded my ubuntu server from 10.10 to 11.10. Everything has gone swimmingly... except for this error.

I have a LVM partition that needs to be fsckd, but every boot I get an error that follows:

"mountall: fsck /boot [563] terminated with status 1"

The system proceeds to boot properly... but I need to figure out what is going to to allow the fsck to properly run on the rest of the system.

My fstab looks like this:
```

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/yoda-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=af2012ac-fae3-4fa2-b622-899eced64fc8 /boot           ext2    defaults     $
/dev/mapper/yoda-swap_1 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/storage/Media  /NAS/Media  xfs  noatime,defaults  0  0
/dev/storage/Misc  /NAS/Misc  ext4  noatime,defaults  0  0
/NAS/Media/DVDMovies  /export/Media/DVDMovies  bind  bind  0
/NAS/Media/Music  /export/Media/Music  bind  bind  0
/NAS/Media/TVShows  /export/Media/TVShows  bind  bind  0
/NAS/Media/Pics  /export/Media/Pics  bind  bind  0
/NAS/Misc  /export/Media/Misc  bind  bind  0
/NAS/Media/mythtv  /export/Media/mythtv  bind  bind  0

```

Any ideas of where to start looking?

---

### Post by thesphynx on 2011-11-16
I am also getting this.  I am not sure but the problem appears related to the mountall package.  It would be nice to get some idea of what's going though.

---

