---
title: "Problem mounting still!"
date: 2010-01-14
forum: General Help
---

### Post by pingu1 on 2010-01-14
Hi!
I am still having trouble mounting devices in Linux.
I got this problem basically after installing/switching from GNOME to KDE,
and then trying to remove KDE, and going back to gnome.

I am trying to mount a samsung phone this time, but I get the message:
"mount: can't find usb in /etc/fstab or /etc/mtab" after writing:
"sudo mount usb".

Anybody know what to do?
My "mtab"-file looks like this:
> /dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/pingu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pingu 0 0My fstab looks like:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3cae7bbe-c971-4c30-b195-517f3aa1b1d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e6f2415-b9cd-45a7-bcce-1d2fdb93313b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0HELP!?

---

### Post by rbc on 2010-01-14
I have never tried to mount a phone so my advice might be completely irrelevant, but you are getting that error because you need to specify the device’s partition, a mountpoint that has been previously created, and (sometimes) a filesystem type and any options. Here is a typical mount command for a flash drive, for instance:
sudo mount /dev/sdb1 /media/usb –o rw –t vfat
With the phone plugged in, open terminal and type:
sudo fdisk –l (that’s a lower case L, not the number 1), and post back.
In the mean time, stay in terminal, and for some light reading, type:
man mount

---

### Post by khelben1979 on 2010-01-15
Exactly what model of the Samsung phone are you trying to connect?

---

