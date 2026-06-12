---
title: "Are these correct mounts in Ubuntu 9.04?"
date: 2009-12-14
forum: General Help
---

### Post by hoosierchick on 2009-12-14
Do these mounts look right?  It seems to me there are too many.  I suspect some kind of intrusion...but I'm so green that I can't tell.  I have not modified any of the /etc/fstab files, etc.

dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8)

---

### Post by Bachstelze on 2009-12-14
Same thing here on Lucid, nothing abnormal.

---

### Post by baddog144 on 2009-12-14
Those look perfectly fine to me ;)

---

