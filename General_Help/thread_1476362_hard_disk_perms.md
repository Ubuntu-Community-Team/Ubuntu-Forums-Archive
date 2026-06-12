---
title: "hard disk perms"
date: 2010-05-07
forum: General Help
---

### Post by W2IBC on 2010-05-07
not sure how this happened. but i have 2 disk drives

hdd 1 is my main drive (160gb) the os is install onto

hdd 2 is a 40gb which is ext3 and used just for backup.

i reinstalled ubuntu 9.04 on here. and totally wiped the main hdd (160gb) and did a clean install. but for some reason my hhd2 (the 40gb) is showing everything owned as root:root every single file is like that.

how can i do a mass file perm change to w2ibc:w2ibc instead of having to change it file by file

---

### Post by dracayr on 2010-05-07
could you please post the output of ```
mount
```. This sounds like the hd was mounted with the wrong umask

dracayr

---

### Post by W2IBC on 2010-05-08
w2ibc@NSA-42876:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/w2ibc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=w2ibc)
/dev/sdb1 on /media/25fe8d54-738b-4372-871d-f7dab1716c8e type ext3 (rw,nosuid,nodev,uhelper=udisks)

---

