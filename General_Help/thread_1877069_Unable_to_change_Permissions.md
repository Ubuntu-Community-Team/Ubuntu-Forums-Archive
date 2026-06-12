---
title: "Unable to change Permissions"
date: 2011-11-07
forum: General Help
---

### Post by shashanksingh on 2011-11-07
Using Ubuntu 11.10.

I can't change the permission of any file owned by me and allow it to be executable. Neither via the command line (even with sudo), nor via nautilus. Both the command and the explorer can do the same in my home folder, but not on any device I mount.

Even when I compiled a simple C file, the execuatable made by gcc says no permission to execute, neither can I change the permission (thats how I came to know about this problem).


Is this a bug?

---

### Post by WasMeHere on 2011-11-07
Hi shashanksingh,

Are your files in an NTFS partition? How is it mounted?

Please post the content of the file /etc/mtab and indicate in which partition you have problems!

Have fun finding out :-)
Olle

---

### Post by mcduck on 2011-11-07
That sounds like you are trying to change permissions of files/directories located on a non-Linux/Unix filesystem. For example both FAT and NTFS lack support for Posix permissions, so commands like chown & chmod are useless with them, the filesystem simply has no way to handle such things. Instead permissions for FAt & NTFS are set for the whole filesystem at the time it's mounted.

You should either format the device with a Linux-compatible filesystem, or move the files to such filesystem.

---

### Post by shashanksingh on 2011-11-07
> **Olle Wiklund said:**
> Hi shashanksingh,

Are your files in an NTFS partition? How is it mounted?

Please post the content of the file /etc/mtab and indicate in which partition you have problems!

Have fun finding out :-)
Olle

```
/dev/sdb5 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdb3 /home ext4 rw,commit=0 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/shashank/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=shashank 0 0
/dev/sdb2 /media/Jupiter fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sdb1 /media/7E2E78292E77D89B fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

```

Im having problems with /dev/sdb2

> **mcduck said:**
> That sounds like you are trying to change permissions of files/directories located on a non-Linux/Unix filesystem. For example both FAT and NTFS lack support for Posix permissions, so commands like chown & chmod are useless with them, the filesystem simply has no way to handle such things. Instead permissions for FAt & NTFS are set for the whole filesystem at the time it's mounted.

You should either format the device with a Linux-compatible filesystem, or move the files to such filesystem.

Is there any way I can maybe change a parameter of mounting on fstab or something?

---

### Post by shashanksingh on 2011-11-07
Thanks olle and mcduck

The problem is clear.

Would be glad if you could tell me the way to BY DEFAULT mount it (some setting?) with the permissions, because I want to keep the directory ntfs, so that I can code using both windows and linux.

---

### Post by WasMeHere on 2011-11-07
> **shashanksingh said:**
> Thanks olle and mcduck

The problem is clear.

Would be glad if you could tell me the way to BY DEFAULT mount it (some setting?) with the permissions, because I want to keep the directory ntfs, so that I can code using both windows and linux.

You look at the resulting /etc/mtab when automounting and take away any umask or dmask to allow maximum permissions, when making an /etc/fstab entry for the partition. Browse the internet for 'file permissions linux' (without citation marks) for more details.

---

