---
title: "USB boot problem on other PC's"
date: 2009-11-23
forum: General Help
---

### Post by warmnscsi on 2009-11-23
Hello, I recently installed Ubuntu 9.10 onto my 8gb flash drive on my home computer. The method I used was to unplug the hdd and do a regular install onto the flash drive including boot files to the usb. It works flawlessly on my home PC but when I tried to boot it off 3 different computers I get the same error which tells me there is something wrong:

> Gave up waiting for root device: common problems:
-boot args
-check root delay
-check root
-missing modules
Alert! /dev/sdc1 does not exist dropping to a shell

How can I fix this? Thanks.

---

### Post by wrgb2 on 2009-11-23
The preferred method for booting from a USB stick is to set the bios to boot from USB first.  This may help.

---

### Post by warmnscsi on 2009-11-23
I'm aware of this, thank you.

---

### Post by snowpine on 2009-11-23
Hi there, possibly the drive is not called /dev/sdc on the other computers? (Possibly /dev/sdb or /dev/sdd etc.)

A temporary solution is to manually edit the grub options at boot time; you can press Tab to auto-complete and hopefully find the correct device name.

The permanent solution is to use UUID instead of /dev/sdc ... I am not an expert but maybe this will point you in the right direction: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by warmnscsi on 2009-11-23
That was exactly what I was looking for thank you. Does anyone know where to find configuration file I need to modify?

---

### Post by efflandt on 2009-11-23
The only error (64-bit 9.10 installed on WD Passport from laptop and booted on desktop) is that it could not find a swapfile (by UUID) that was apparently on the hardrive of my laptop.  But I also have a swapfile on the USB drive, so after a pause, it continued and booted fine.

I actually cannot tell which swapfile(s) being used because I forget what size I made them on USB and desktop.  But I think it is just using a large one I made on the Passport in case I run on a PC with no swap, because the desktop drive spun down from inactivity.

```

**free**
             total       used       free     shared    buffers     cached
Mem:       2058068     367548    1690520          0       9640     101416
-/+ buffers/cache:     256492    1801576
Swap:      4401800          0    4401800

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=2b7a433f-0441-46ff-90a6-936e2c6d7347 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=b82de8c8-fb6d-47a1-bdff-997b0e00f28a none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=6d15ee0b-749f-4474-acb7-6bbc0613ad23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

**mount**
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/efflandt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=efflandt)
/dev/sdb1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```Note that anything in fstab that mounts with /dev/whatever instead of UUID or if the UUID is unavailable may fail.  I should probably remove the entry using swap on /dev/hda3 which may not exist on another PC.

If your USB drive was sda when installed, and sdb or something else when booted along with internal drive, that could explain your errors.  But you have to be careful installing to a USB drive when you have an internal drive, because near the end of install you have to use the **Advanced** button to put grub/grub2 on the USB drive instead of default internal drive mbr.

---

