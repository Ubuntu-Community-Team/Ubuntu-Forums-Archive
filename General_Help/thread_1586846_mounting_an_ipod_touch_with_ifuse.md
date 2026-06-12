---
title: "mounting an ipod touch with ifuse"
date: 2010-10-02
forum: General Help
---

### Post by someitalian123 on 2010-10-02
I think i might be missing dependence or something because whenever I try

 sudo ifuse /mnt/ipod

I get no errors but I find nothing in the mnt folder, the ipod folder apparently just disappeared, and I can't load with gtkpod. I'm a missing a step to the mounting?

---

### Post by mr_luksom on 2010-10-03
if you enter just ```
 mount 
```

what do you see? Can you post it?

---

### Post by someitalian123 on 2010-10-04
If i just enter mount and nothing else this is what I get.

linux@linux:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/linux/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=linux)

---

### Post by someitalian123 on 2010-10-06
Anyone have any ideas on what the problem could be?

---

