---
title: "exportfs: scandir /etc/exports.d: No such file or directory"
date: 2012-01-02
forum: General Help
---

### Post by 65 mustang on 2012-01-02
I want to export a dir with NFS on my system.  I have done the folowing.
```

apt-get install nfs-kernel-server nfs-common

```

```

cat /etc/exports 

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/root/backups/backup	*(ro,no_subtree_check)

```

```

service nfs-kernel-server restart
 * Stopping NFS kernel daemon                                                                                                          [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                                                    [ OK ] 
 * Exporting directories for NFS kernel daemon...                                                                                             
**[COLOR="Red"]exportfs: scandir /etc/exports.d: No such file or directory[/COLOR]**

                                                                                                                                       [ OK ]
 * Starting NFS kernel daemon                                                                                                          [ OK ]

```

```

showmount -a localhost
All mount points on localhost:

```

Nothing is being exported and shared.  Im guessing it is related to the **[COLOR="Red"]exportfs: scandir /etc/exports.d: No such file or directory[/COLOR]** message.  Any ideas?

---

### Post by 65 mustang on 2012-01-02
Interesting.  The dirrectory it is looking for does not exist.

```

ls /etc/exports.d
ls: cannot access /etc/exports.d: No such file or directory

```

---

### Post by 65 mustang on 2012-01-02
My share was working all along.  I was just using the wrong options with showmount.

```

showmount -e localhost
Export list for localhost:
/root/backups/backup *

```

On a side note this still looks like a bug...
```
exportfs: scandir /etc/exports.d: No such file or directory
```

---

### Post by Juxe on 2012-04-08
solution:
sudo mkdir /etc/exports.d

---

