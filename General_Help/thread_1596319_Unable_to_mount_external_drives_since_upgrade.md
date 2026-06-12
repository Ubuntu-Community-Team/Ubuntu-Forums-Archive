---
title: "Unable to mount external drives since upgrade"
date: 2010-10-14
forum: General Help
---

### Post by kenny99 on 2010-10-14
Hi, since I ran a system upgrade last week I haven't been able to mount an external drive - my iphone, and a server on my work LAN - both of which were mounting no problem previously. I was running ubuntu at the time of the upgrade and since have switched from GNOME to KDE, but that won't be the issue as the mount problem was happening before I switched to KDE. 

Here are some of the results I am getting:

```
lsmod | grep usb
usbhid                 41084  0 
hid                    83472  1 usbhid
usb_storage            49961  0
``` 

```
cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb1 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

---

