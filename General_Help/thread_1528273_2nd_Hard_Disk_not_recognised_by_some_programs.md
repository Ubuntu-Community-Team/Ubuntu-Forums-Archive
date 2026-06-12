---
title: "2nd Hard Disk not recognised by some programs"
date: 2010-07-10
forum: General Help
---

### Post by CoolJohnB on 2010-07-10
I have 2 Hard Disks in my computer both of them show in File & Folders, and they are both formated by Ububtu, I use the 2nd one for my Data storage as it's the larger of the two.

The problem I have is that certain programs just don't see it! For example Album Shaper sees the boot drive but not the 2nd one which has all my photo's on it.  OpenOffice is not a problem it sees both drives. But there are a few programs that just don't see it.

Does anyone know a solution to this?

Any help will be much appreciated.

---

### Post by oldos2er on 2010-07-10
What's the second drive's mount point?

---

### Post by CoolJohnB on 2010-07-10
I am new to Ubuntu how do I find it's mountpoint? Thanks

---

### Post by oldos2er on 2010-07-10
Type **mount** in a terminal (Applications, Accessories, Terminal), and post the output here.

---

### Post by CoolJohnB on 2010-07-10
Thanks, here it is:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/sdb1 on /media/Data type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by oldos2er on 2010-07-10
So when you're in the program 'Album Shaper,' point it to /media/Data, which normally you'd run from a File, Open menu.

---

### Post by CoolJohnB on 2010-07-10
Thank you very much, problem solved!  Once again I have to say how very good this forum is, there really is no better help system. Awesome!

---

