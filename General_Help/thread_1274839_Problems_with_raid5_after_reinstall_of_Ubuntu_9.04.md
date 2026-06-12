---
title: "Problems with raid5 after reinstall of Ubuntu 9.04"
date: 2009-09-25
forum: General Help
---

### Post by odinb on 2009-09-25
Hi!

Had a nasty disk crash on my rootdisk, and had to reinstall my system.

Now my raid5 system (my data-storage) will not come up/ mount.

Have run a "sudo mdadm --assemble --scan", and then "sudo fdisk -l /dev/md0" and get this back:

Disk /dev/md0: 1200.2 GB, 1200257236992 bytes
2 heads, 4 sectors/track, 293031552 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

The raid consists of sda1, sdb1 sdc1 sde1, and was working before the root-disk crash.

"sudo mount /dev/md0" comes back with:
mount: can't find /dev/md0 in /etc/fstab or /etc/mtab



Any ideas?

Thanks!

---

### Post by odinb on 2009-09-25
Nevermind,  I did not create the mount points in /media...

All is good now, I hope!

---

