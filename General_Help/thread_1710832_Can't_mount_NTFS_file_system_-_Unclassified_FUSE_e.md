---
title: "Can't mount NTFS file system - Unclassified FUSE error"
date: 2011-03-20
forum: General Help
---

### Post by mpetrovsky on 2011-03-20
For some bizarre reason my system has stopped allowing me to mount NTFS file systems at boot time.

So I've tried mounting it manually and get no joy. It took a while to realise that the mount command was returning error code 21 -  Unclassified FUSE error

The frustrating thing is that there is nothing in the log files to point to what the error could be [/var/log/*]

This is what I do:

```
root: ~# mount.ntfs /dev/sdd1 /tmp/2 -o nls=utf8,ro,umask=0222
root: ~# echo $?
21
root: ~# mount.ntfs-3g /dev/sdd1 /tmp/2 -o nls=utf8,ro,umask=0222
root: ~# echo $?
21
root: ~# mount.ntfs-fuse /dev/sdd1 /tmp/2 -o nls=utf8,ro,umask=0222
fuse_mount failed.
Unmounting /dev/sdd1 (mjp-ext-1a)
root: ~#
```

and my system config is:
```

root: ~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
root: ~# uname -a
Linux xxxx 2.6.35-22-generic-pae #35~lucid1-Ubuntu SMP Tue Nov 23 23:00:56 UTC 2010 i686 GNU/Linux

root: ~# cat /proc/filesystems |grep 'fuse\|ntfs'
nodev	fuse
	fuseblk
nodev	fusectl
	ntfs

root: ~# lsmod |grep ntfs
ntfs                   95463  0 

```

Hope someone can give me a pointer to what the isuse could be. 

Thanks, Martin

---

### Post by mpetrovsky on 2011-03-20
Found this - [https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/727668](https://bugs.launchpad.net/ubuntu/+source/fuse/+bug/727668)

and after downgrading libfuse from 2.8.1-1.1ubuntu3.1 to 2.8.1-1.1ubuntu2 has resolved the issue!

Yay!

---

