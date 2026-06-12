---
title: "SSHFS in fstab issue"
date: 2011-09-05
forum: General Help
---

### Post by pieroxy on 2011-09-05
I have an issue with sshfs whenever it is mounted from /etc/fstab. Here is what I did:

```

$ sshfs -o port=2226 home-server:/path /media/mountpoint

```
This works fine and I can read/write from the mountpoint with no issue. Now, if I add a line in /etc/fstab like this:
```

sshfs#pieroxy@home-server:/path /media/mountpoint fuse user,port=2226 0 0

```
Here is the result:

```

$ sudo mount /media/mountpoint
$ ls /media/mountpoint
ls: cannot access /media/mountpoint: Permission denied
$ ls -l /media/
ls: cannot access /media/mountpoint: Permission denied
total 76
d?????????  ? ?       ?           ?                ? mountpoint
(........)

```

Does anyone has an idea of what is wrong here?

---

### Post by pieroxy on 2011-09-09
Ok, so it has gotten worse as today I cannot mount my share even manually. When running the command line I get the same result as the fstab.

Ont funny thing is the following:
```
$ sudo sshfs -p 2226 pieroxy@home-server:/path/ /media/mountpoint/
$ ll /media/
ls: cannot access /media/mountpoint: Permission denied
(...)
d?????????  ? ?       ?           ?                ? mountpoint/
(...)
$ sudo ls -l /media/
(...)
drwxrwxrwx  1 pieroxy pieroxy  4096 2011-07-31 22:13 mountpoint
(...)
$ 

```

Does anyone has a clue?

---

### Post by pwhyte on 2011-10-16
I ran into this as well, it is not a 'good' solution but a user by the name of 'grawity' posted the below on another site (link below as well).  Hope this helps.

sshfs is a FUSE-based filesystem, and the FUSE layer does not allow other users to access its mounts by default, for security purposes. You have allow_other in options, but it will be ignored until you also edit /etc/fuse.conf to include user_allow_other

I found the advice here:
[http://superuser.com/questions/262778/set-proper-rights-for-sshfs-mountpoint-so-it-can-be-shared-with-samba](http://superuser.com/questions/262778/set-proper-rights-for-sshfs-mountpoint-so-it-can-be-shared-with-samba)

---

### Post by pieroxy on 2011-10-29
Wow... I didn't expect any answer to this message this late after my posting !!! Thanks. 

I added allow_other in my fstab line and it seems to be working. Will follow up if I need to do anything else.

Thanks again!

---

