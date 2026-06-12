---
title: "Prevent updatedb on WebDav mount, need help"
date: 2010-05-17
forum: General Help
---

### Post by Saorex on 2010-05-17
Hi guys. I have a WebDav (davfs2) mounted in /home/myuser/mydavmount

I would like to prevent updatedb from indexing the content of the mounted drive. I tried editing /etc/updatedb.conf and setting the following:

```
PRUNEPATHS="/tmp /var/spool /media /home/myuser/mydavmount"
```

also tried these:

```
PRUNEFS="NFS nfs nfs4 [...] davfs"

and

PRUNEFS="NFS nfs nfs4 [...] davfs2"

also

PRUNEFS="NFS nfs nfs4 [...] fuse.davfs"
```

None of these worked. Anyone has an idea?

Thanks a lot!

---

### Post by Saorex on 2010-05-18
Anyone has an idea? At least a hint... Thanks!

---

### Post by Saorex on 2011-03-02
Just wanted to let everyone know I found a solution for that. It was pretty simple in fact:

```
sudo nano /etc/updatedb.conf
```

Add the path to your WebDAV mount to PRUNEPATHS list:
```
PRUNEPATHS="/tmp /var/spool /media /path_to_webdav_mount"
```

Hope this will help someone someday. ;)

---

