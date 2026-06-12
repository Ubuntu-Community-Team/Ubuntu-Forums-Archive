---
title: "Can't mount data dvd..."
date: 2010-06-14
forum: General Help
---

### Post by killabee44 on 2010-06-14
Guys,

On DVD drive (fresh Lucid 10.04 install) I can't mount a data dvd with pics on it. Movie DVD's, Data CD's mount fine.

It looks like in Nautilus, the system tries to mount the dvd drive and does for a second, but it's called:

"VRD_MC3"

then, the mount disappears and I can't get to the data. This dvd mounts fine in windows so Im not sure what's up.

If anyone knows how to troubleshoot this please let me know. Thanks.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4    errors=remount-ro 0       1
/dev/sdc6       /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0
```

 ls -l /dev/{cd,dvd}*:

```

lrwxrwxrwx 1 root root 3 2010-06-14 00:28 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 00:28 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 00:28 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-06-14 00:28 /dev/dvdrw -> sr0

```

---

