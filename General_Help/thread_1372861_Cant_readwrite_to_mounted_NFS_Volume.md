---
title: "Cant read/write to mounted NFS Volume"
date: 2010-01-05
forum: General Help
---

### Post by Linux000 on 2010-01-05
Hi,

I have just set up a NFS server in ubuntu server, and I can't make the client work. In /media (on the client) there is a directory called Storage it's permissions are 777 and the owner is my user. However when I run
```
sudo mount -t nfs 192.168.1.143:/media/Storage /media/Storage
```
the mount succeeds (df shows the file mounted)but the file perms change and natulis wont let me do anything except read the files.

---

### Post by jocko on 2010-01-05
Are you sure the folder is shared with read/write permissions?
What does the /etc/exports file in the server machine look like?

---

### Post by Linux000 on 2010-01-05
the line that isn't commented is like this

```
/media/Storage 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
```

The volume is mounted to /media/Storage on the server, as well as the client.

---

### Post by Linux000 on 2010-01-05
Also the directory (Storage in this case) has the perms change, before the out of ls -al Storage is 
```

drwxr-xr-x  2 michael michael 4096 2010-01-05 01:40 Storage

```
after the mount
```

drwxr-xr-x  3 root root 4096 2010-01-05 00:40 Storage

```

---

### Post by jocko on 2010-01-05
Hmmm... Ok. That looks correct.
I can't help you then. Good luck.

---

### Post by Linux000 on 2010-01-05
Thanks for trying.

---

### Post by Linux000 on 2010-01-05
For future reference, the File Permissions on the client depend on the file permissions on the host, even if the exports file has rw.

---

