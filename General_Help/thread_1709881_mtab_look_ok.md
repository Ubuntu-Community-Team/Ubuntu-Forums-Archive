---
title: "mtab look ok?"
date: 2011-03-19
forum: General Help
---

### Post by mynot on 2011-03-19
Can someone tell me if there's something wrong with this mtab, especially the line beginning with "udev"? I'm getting a boot error concerning "Mounting none on /dev failed". Although that has been discussed on various forums, none of the solutions seem relevant. I'm just wondering if that udev line could cause it.
/dev/sda1 / ext3 rw,relatime,errors=remount-ro,commit=0 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/sdb2 /media/windata fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/winboot fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/tony/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=tony 0 0

Thanks
Tony

---

