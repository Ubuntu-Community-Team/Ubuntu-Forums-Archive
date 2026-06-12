---
title: "nfs-share export internal hard drive"
date: 2012-08-07
forum: General Help
---

### Post by 8301 on 2012-08-07
Hello

I have 5 hard drives that I would like to share via nfs to my laptop. 

There is no problem to share a directory placed under "/home/" for example:
/home/sebastian/Downloads

But when I open the Movie folder, which is the mount point for /dev/sda1, it is empty! No movies for me :(

So I edit /etc/exports and try to export /dev/sda1/ and restart NFS server then I receive this error message:

"exportfs: Failed to stat /dev/sda1/: Not a directory"

So the question is how can I export/share internal hard drives via NFS?

Thanks in advance

---

### Post by Zill on 2012-08-07
> **8301 said:**
> I have 5 hard drives that I would like to share via nfs to my laptop. 

There is no problem to share a directory placed under "/home/" for example:
/home/sebastian/Downloads

But when I open the Movie folder, which is the mount point for /dev/sda1, it is empty! No movies for me...
If you cannot see your movies on the local machine then this seems to indicate that your fstab needs to be edited to mount the additional hard drives to your filesystem.

When these drives are mounted locally it should then be possible to export via nfs.

---

### Post by papibe on 2012-08-07
Hi 8301.

I don't think you should export the device itself, but the mount point.

Could you post the result of these commands on the server?
```
cat /etc/exports

mount -l
```

Regards

---

### Post by 8301 on 2012-08-13
Ops my beginner mistake I had spaces on the folder names. So everything is now working.

---

