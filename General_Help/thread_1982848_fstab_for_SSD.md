---
title: "fstab for SSD"
date: 2012-05-19
forum: General Help
---

### Post by lolpenguin on 2012-05-19
I (hopefully) have disabled access times, enabled discard, moved temporary folders to ram, changed the scheduler to deadline. I've symlinked .cache to a mech hard drive, swap is on mech hard drive. Is there anything else I need to do to stop unneccesary writes to my SSD?
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=4c5e3194-3519-4e92-bda3-0a64ee7e1cd3 /               ext4    noatime,nodiratime,discard,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=94eaae07-8632-4411-96d7-70917b1aa627 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# tmp in ram
tmpfs	/tmp		tmpfs	defaults,noatime,mode=1777	0	0
tmpfs 	/var/spool	tmpfs	defaults,noatime,mode=1777	0	0
tmpfs	/var/tmp	tmpfs	defaults,noatime,mode=1777	0	0

```
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo deadline > /sys/block/sdb/queue/scheduler
echo 0 > /proc/sys/vm/swappiness

exit 0

```

---

### Post by Cheesemill on 2012-05-19
Looks good to me, it's pretty much exactly the same as my setup.

In your fstab you don't have to use the nodiratime option, it is already implied by using noatime.

---

### Post by 2F4U on 2012-05-19
If the ssd is the only disk in your system, you can set the I/O scheduler through a kernel parameter, for example

elevator=deadline

in the grub configuration.

---

### Post by Cheesemill on 2012-05-19
> **2F4U said:**
> If the ssd is the only disk in your system, you can set the I/O scheduler through a kernel parameter, for example

elevator=deadline

in the grub configuration.

> I've symlinked .cache to a mech hard drive, swap is on mech hard drive.

:)

---

### Post by lolpenguin on 2012-05-20
I've had to move .cache back, as the symlink complained that it was broken when it was not, and annoyingly (possibly some bug) makes my computer think that the hard drive is full when it has a good 200GiB left on the partition. I've disabled most of the caches in the meantime. I'll have to see what is causing this!!

---

### Post by chocklet on 2012-05-20
You've probably already considered the following measures to minimize writes to your SSD, but I'll to mention them anyway...

<> Put all of /var on the spinner.  My mechanical drive is sdb (I think that yours is sda).  This is from my fstab...

# /var was on /dev/sdb7 during installation
UUID=48815369-1d93-4e39-ad8d-e29fe32f32c0 /var            ext4    defaults        0       2

<> Put all your data files on the spinner, instead of in Home (which apparently is on your SSD).  There are several ways of setting it up.  In fact you don't have to do anything in the fstab and your data partition will be  easily mounted.  I decided to name/label the partition on my data drive to make things more understandable, and to mount it at boot.  (again, sdb on my PC)  From my fstab...

# /media/i11data was on /dev/sdb11 during installation
UUID=62af902f-7015-42b4-899d-c63a766e9bfb /media/i11data  ext4    defaults        0       2

---

### Post by jim_deadlock on 2012-05-20
If I add these to my fstab is it then safe to delete these directories off my SDD?

```
# tmp in ram
tmpfs	/tmp		tmpfs	defaults,noatime,mode=1777	0	0
tmpfs 	/var/spool	tmpfs	defaults,noatime,mode=1777	0	0
tmpfs	/var/tmp	tmpfs	defaults,noatime,mode=1777	0	0
```

---

### Post by jim_deadlock on 2012-05-20
Looks like this line made my cron jobs disappear so I don't know why anyone would recommend this.

```
tmpfs 	/var/spool	tmpfs	defaults,noatime,mode=1777	0	0
```

---

