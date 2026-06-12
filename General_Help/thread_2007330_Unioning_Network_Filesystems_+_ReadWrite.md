---
title: "Unioning Network Filesystems + Read/Write"
date: 2012-06-20
forum: General Help
---

### Post by spartan21 on 2012-06-20
As the thread title suggests, I am trying to union two remote filesystems on a local machine and have read/write access to the union.
 
So far, I have successfully individually mounted the network FSs as NFS, and I have unioned them as aufs. The command I use to perform the union is:
 
```
sudo mount -t aufs -o br:/path/to/mount1:/path/to/mount2 none /mountpoint
```
 
When executed, I receive this:
 
```
mount: block device none is write protected, mounting read-only
```
 
I have also tried the following command, but receive the subsequent errors:
 
```
sudo mount -t aufs -o br:/path/to/mount1=rw:/path/to/mount2=rw none /mountpoint
 
mount: block device none is write protected, mounting read-only
mount: cannot mount block device none read-only

```
 
Without using chmod, how should I go about unioning the two NFSs as aufs read/write? At this point I'm lost, so any help would be very appreciated. Thanks!

---

### Post by spartan21 on 2012-06-20
If it helps, I'm running Ubuntu 11.1.0 on all three systems.

---

### Post by spartan21 on 2012-06-22
bump

---

