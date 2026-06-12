---
title: "Editing fstab"
date: 2010-06-23
forum: General Help
---

### Post by esullivan on 2010-06-23
I am trying to edit fstab to auto mount a couple of windows shares.  I have this but it doesn't work.  What am I doing wrong?


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   		<type>  <options>       	<dump>  <pass>
proc            /proc           		proc    nodev,noexec,nosuid 	0       0
/dev/sda1       /               		ext4    errors=remount-ro 	0       1
//192.168.1.3/video	/home/evan/Videos	smbfs	0	0
//192.168.1.3/music	/home/evan/Music	smbfs	0	0
# swap was on /dev/sda5 during installation
UUID=6cc46266-db89-4d7b-a0b7-960c184502e9 none            swap    sw            0       0
```

---

### Post by cariboo on 2010-06-23
smbfs is depreciated, use cifs. Have a look at [this]("http://ubuntuforums.org/showthread.php?t=288534") howto.

---

### Post by esullivan on 2010-06-23
Awesome, got it to work, thanks!

---

