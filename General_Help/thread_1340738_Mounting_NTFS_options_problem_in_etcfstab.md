---
title: "Mounting NTFS options problem in /etc/fstab"
date: 2009-11-28
forum: General Help
---

### Post by ttilberg on 2009-11-28
Relevant line in current fstab:

# Entry for /dev/sda1 :
UUID=4E28D07928D0620F /media/ntfs ntfs defaults,nls=utf8,umask=000,users 0 0

It is the correct UUID, as the drive mounts using mount -a with it in, and doesn't with it commented out. The part I am curious by is this (irrelevant lines removed):

ttilberg@ragnarok:/etc$ mount
/dev/sda1 on /media/ntfs type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


The reason I am curious is because I am looking to add my external and was checking settings, only to notice that the settings I thought I was mounting with were not the ones the system was using.

Any hints as to why the options list, especially the "type" is different? I guess I expected that line to match what my fstab used.

Thanks,
Tim

---

### Post by prshah on 2009-11-28
> **ttilberg said:**
> /dev/sda1 on /media/ntfs type fuseblk 

fuse (Filesystem in Userspace) is a module that allows a filesystem to be loaded and manipulated without the need for kernel level drivers.

This means that it can be adapted to any number of filesystems without needing to have support for all the filesystems at the kernel level.

fuseblk indicates that the mounted drive is a block device handled by fuse. 

This is the preferred way to handle non-linux filesystems, though even linux filesystems can be handled by fuse (and in fact are in the cases of external drives).

From 8.10 onwards, Ubuntu is moving to eliminate dependence on static configuration files such as /etc/fstab and /etc/X11/xorg.conf. To use your external casually in Ubuntu, just plug it in, there is no need to muck about with the fstab. However, if you want it automounted, then you need to have an entry in the /etc/fstab, *similar* to the following:```

# Entry for external: Find UUID with "sudo blkid" command
UUID=4B50A07928D0842D /media/external ntfs defaults,auto,umask=007,gid=46 0 0
```

In the above line, please note that the gid is that of the "fuse" group. It may vary on your system. This will ensure that your external is accessible to any member of the fuse group (default is everybody).

---

