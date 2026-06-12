---
title: "Drives not ready to assemble RAID5 at boot"
date: 2012-05-06
forum: General Help
---

### Post by SuperLou on 2012-05-06
I have a raid 5 mdadm configuration made up of 3 drives.  Inside Ubuntu (once the drives are ready), all of the mdadm assemble/stop/detail commands seem to work fine.

On Ubuntu 11.10 and now 12.04, the system would halt at the initramfs prompt until I typed exit because the drives are not ready to be assembled.  In the dmesg log, I get the following notices:

```

[    3.632828] md: raid6 personality registered for level 6
[    3.632893] md: raid5 personality registered for level 5
[    3.632957] md: raid4 personality registered for level 4
[    3.636969] md: raid10 personality registered for level 10
[    3.654044] bio: create slab <bio-1> at 1
[    3.654117] md/raid:md0: device sdb1 operational as raid disk 2
[    3.654461] md/raid:md0: allocated 3228kB
[    3.654556] md/raid:md0: not enough operational devices (2/3 failed)
[    3.654631] RAID conf printout:
[    3.654632]  --- level:5 rd:3 wd:1
[    3.654634]  disk 2, o:1, dev:sdb1
[    3.654906] md/raid:md0: failed to run raid set.
[    3.654969] md: pers->run() failed ...

```
```

```
Also, later in the boot process it complains about /dev/md0 already being in use, though I can't find the log that contains that message.

The problem seems similar to [http://ubuntuforums.org/showthread.php?t=1799204&highlight=mdadm+drives+ready](http://ubuntuforums.org/showthread.php?t=1799204&highlight=mdadm+drives+ready) from 2011 and related to [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681) which is listed as fixed.  All 3 drives pass SMART checks as healthy, so I don't think the drives are actually damaged (plus mdadm addresses them with no problem after boot).

My fstab and mdadm.conf are as follows:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=47719a6e-6b2f-4fde-9069-1a8e05e0dede /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d7afb1d6-c939-4b29-862c-cd821f7a0089 none            swap    sw              0       0
/dev/md0	/media/SRAID1	ext4	defaults,nobootwait	0	2

```

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]my.email@address.com[/email] # This doesn't work, but doesn't seem related to the problem

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=1.2 UUID=6bbceb65:d8ad5912:92d5a92b:981a6c16 name=bestever:0

# This file was auto-generated on Sun, 29 Apr 2012 10:03:36 -0400
# by mkconf $Id$

```


I would greatly appreciate any tips.  Let me know if there's additional info I can provide.

Thanks,
Louis

---

