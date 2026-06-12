---
title: "initscripts - mount virtual filesystem"
date: 2011-07-23
forum: General Help
---

### Post by arssus on 2011-07-23
Hi all,

Does anybody know which script/package mounts the virtual filesystem at boot time in order to get all filesystems mounted (ie: tmpfs, sysfs, ramfs, devpts, etc..)?

I have noticed that the script /etc/init.d/mountkernfs.sh have some instructions about mounting tmpfs on /var directory but how do you get it to work all together?

I'm looking for getting something like this:

user@linuxbox1:~$ mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda4 on /home type ext4 (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sda2 on /media/facd5931-b25a-45e9-912a-5282ae45ee3a type ext4 (rw)

Rather than this:

user@linuxbox2:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)

Obviously these outputs belong to two different types of installations, first one is the output from a linuxmint 10 install and the second one is from Maverick server install.

I know it could be done by adding entries on the fstab but I'd like to do it with the initscripts coded for that purpose instead...

I'd appreciate some answers... Thanks

---

