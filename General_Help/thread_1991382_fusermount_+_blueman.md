---
title: "fusermount + blueman"
date: 2012-05-30
forum: General Help
---

### Post by Farinet on 2012-05-30
lubuntu 12.04 ppc:

I'm having a problem with bluetooth trying to connect a cell phone or a camera to transfer files from the device to the computer. I use blueman. When i try to transfer files, blueman is dead slow, apparently. 

Then, in the log file i see this msg:

> fusermount: entry for ~/Bluetooth-00:25:48:3A:A9:58 not found in /etc/mtabWhere is the error?

My mtab file looks like this:

> /dev/sdb3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0TIA

---

