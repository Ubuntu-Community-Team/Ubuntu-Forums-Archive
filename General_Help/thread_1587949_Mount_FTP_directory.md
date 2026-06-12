---
title: "Mount FTP directory"
date: 2010-10-04
forum: General Help
---

### Post by danielrs on 2010-10-04
I've been trying to mount ftp on a directory, using curlftpfs, but when I run:

```
curlftpfs user:pass@server /mnt/mount-point
```

I get the error:

```
fuse: device not found, try 'modprobe fuse' first
```

And when I run it, I get:

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Could not load /lib/modules/2.6.32-dyomin.1/modules.dep: No such file or directory
```

After searching on Google, I found a forum post somewhere saying to run

```
mknod /dev/fuse c 10 229
```

After that when I run the mount command ) get the error:
```
fuse: failed to open /dev/fuse: Operation not permitted
```

Can anyone help me?

---

### Post by surfer on 2010-10-04
did you add yourself (i.e. your username) to the fuse group?

---

### Post by danielrs on 2010-10-04
I don't know :-k but I'm running as root :oops:

---

### Post by danielrs on 2010-10-04
Root was not on the fuse group, but now it is and I'm getting the same error

---

### Post by danielrs on 2010-10-04
No one can help me?:(

---

