---
title: "Automount partion on startup"
date: 2011-12-26
forum: General Help
---

### Post by raghav.venky on 2011-12-26
I want to automount a NTFS partion on startup. But the partion is not listed in fstab. What should I do?

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=32da05bf-5145-4c1a-9841-da0350bba847 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=87807a81-e3f5-48d6-9aa8-813aa662fded none            swap    sw              0       0


```

---

