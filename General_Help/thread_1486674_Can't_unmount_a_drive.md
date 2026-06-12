---
title: "Can't unmount a drive"
date: 2010-05-18
forum: General Help
---

### Post by oopsie on 2010-05-18
I get this message when I try to unmount a drive. I have no idea why I have this problem. It's always worked in the past.

[http://img694.imageshack.us/img694/4495/blahbb.png](http://img694.imageshack.us/img694/4495/blahbb.png)

---

### Post by mikewhatever on 2010-05-18
How about the output of the following:

cat /proc/mounts

---

### Post by Jakiejake on 2010-05-18
Um...
Tried Formatting or longing in as Root?

---

### Post by oopsie on 2010-05-20
> **mikewhatever said:**
> How about the output of the following:

cat /proc/mounts

```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=507400k,nr_inodes=126850,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/a4df3102-131d-4a2d-bfe2-fdd5ad388d9e / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/me/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sda1 /media/New\040Volume fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0

```

I've rebooted ubuntu a few times since the problem first occurred. But every time I mount a hard drive, I can't unmount it afterwards.

Also, ubuntu seems slower on booting recently

---

### Post by Nythain on 2010-05-20
silly question, have you tried this in a terminal...

sudo umount /path/to/mounted/device

---

### Post by akakingess on 2010-05-20
I'm having a similar issue with unmounting an extra internal drive that I have automatically mounting upon boot, and also have had that issue with trying to unmount/eject a USB flash drive.

---

### Post by oopsie on 2010-05-20
> **Nythain said:**
> silly question, have you tried this in a terminal...

sudo umount /path/to/mounted/device

But why does it need sudo now, when it didn't three days ago? And is it connected with my ubuntu being slow?

---

