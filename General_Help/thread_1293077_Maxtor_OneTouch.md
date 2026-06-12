---
title: "Maxtor OneTouch"
date: 2009-10-16
forum: General Help
---

### Post by DoubleCross on 2009-10-16
My external HDD will not mount in 9.10. How can I get the device to register so that i can access my files before I replace my internal hard drive.

Any suggestions?

---

### Post by wilee-nilee on 2009-10-16
> **DoubleCross said:**
> My external HDD will not mount in 9.10. How can I get the device to register so that i can access my files before I replace my internal hard drive.
 
Any suggestions?
 
My Maxtor one touch runs fine in 9.10, I never changed the partition I just left it as NTFS, it will only encrypt through windows though. Have you changed the partition, and are you giving it a couple of minutes to register and are looking under the computer area for mounted stuff to see if it is mounted or just waiting for a desktop icon which will never appear if your running conky.

---

### Post by mikewhatever on 2009-10-16
Assuming the file system is ntfs, you may need to check it from Windows.

---

### Post by blueridgedog on 2009-10-16
We can try and mount it manually.  Can you post the output of
```

sudo fdisk -l 
```

and 

```
mount
```

---

### Post by DoubleCross on 2009-10-17
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

mount:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=664)
gvfs-fuse-daemon on /home/danielcairo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=danielcairo)

It still wont mount. I know it should work fine in 9.10 because it was working fine in 9.10. I dont know what happened to it.

---

### Post by mikewhatever on 2009-10-17
sudo fdisk -l

The last letter is a small 'L' and not number 1. Look similar, but they are not the same.

---

### Post by scouser73 on 2009-10-17
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

