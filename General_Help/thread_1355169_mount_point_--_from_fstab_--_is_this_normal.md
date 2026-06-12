---
title: "mount point -- from fstab -- is this normal ??"
date: 2009-12-14
forum: General Help
---

### Post by hoosierchick on 2009-12-14
I am new to Ubuntu -- and would like to know if this is a default mount listing.  I used a live cd to install, but I feel like there are some security issues on my laptop.  Please let me know if any of these look fishy.  Thanks!

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-17-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mom/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mom 0 0

---

### Post by bodhi.zazen on 2009-12-14
I do not see any problem there, what are you concerned with ?

---

