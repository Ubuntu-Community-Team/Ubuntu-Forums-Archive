---
title: "programs crash and system gets unstable"
date: 2010-12-02
forum: General Help
---

### Post by obbe on 2010-12-02
Hi, I'm using Ubuntu 10.10 on a 120gb SDD Ocz Vertex2, my problem is that sometimes (very often) when I boot up the system I find it to be very unstable, every program crashes and the only solution is to reboot the computer; when I reboot it, it may be unstable again or stable (like now), I think it has something to do with the SSD, of course I added discard and noatime or relatime, here's my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=da6ecc93-3ab8-4afa-9c2d-767a10f94da1 /               ext4    discard,relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5107cbc4-0695-41a3-956b-4a9c18860011 none            swap    sw              0       0
```

Any help? Thanks..

---

