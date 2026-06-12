---
title: "Software Raid &amp; /home"
date: 2009-10-02
forum: General Help
---

### Post by redilyn on 2009-10-02
Hi,

For some reason my /home array is not mounting on boot.

There are 2 arrays configured, one for / and one for /home

/ mounts fine on boot.

When I get to the GDM login screen I have to switch to terminal and mount /dev/md1p1 manually before I can log in.

Any idea how I can get this to mount on boot?

mdadm.conf
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=3 UUID=d9c151d7:9dcb3869:61d29a67:8b934f45
ARRAY /dev/md1 level=raid0 num-devices=3 UUID=a75426b0:4e33d657:94475e3c:0fea1594

# This file was auto-generated on Thu, 01 Oct 2009 12:38:10 -0300
# by mkconf $Id$
```

fstab
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md0p1 during installation
UUID=54ac36e2-33ca-4a69-8037-8db88db69429 /               ext3    noatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=27fa567f-f47b-44a5-961f-ac35a0d2e672 /boot           ext3    noatime         0       2
# /home was on /dev/md1p1 during installation
UUID=a2719327-2359-4c4a-bb6b-97b978c76da8 /home           ext3    noatime         0       2
# /media/disk was on /dev/sdc3 during installation
UUID=a2cf2504-22a9-431a-8daa-94abc1b52990 /media/disk     ext3    noatime         0       2
# /media/transfer was on /dev/sda5 during installation
UUID=6e070a9a-b608-45a6-b9ac-a97710f37579 /media/transfer ext3    noatime         0       2

```

Thanks

---

### Post by i.r.id10t on 2009-10-02
# /home was on /dev/md1p1 during installation
UUID=a2719327-2359-4c4a-bb6b-97b978c76da8 /home 

Make sure this is still the UUID for it using blkid


Also, run dmesg and look thru it for errors relating to mounting, etc.

---

### Post by Giblet5 on 2009-10-02
If you're using dmraid, it has to start before the mount is attempted.

You can try to weed out which rc files need to be tweaked, or you can hack it by adding ```
/etc/init.d/dmraid start
/bin/mount -a
``` to the /etc/rc.local file, right before that "exit 0".

---

### Post by redilyn on 2009-10-03
Okay,

blkid returns a matching UUID to fstab

dmesg shows no mount errors

How would I know if I am using dmraid?

I would think it is starting in time since the / array is mounting fine.

---

