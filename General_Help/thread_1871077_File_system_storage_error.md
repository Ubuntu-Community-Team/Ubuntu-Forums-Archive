---
title: "File system storage error"
date: 2011-10-28
forum: General Help
---

### Post by raphaelb96 on 2011-10-28
when i click on properties of the file system it says i have 7.7 gb left but i know i don't. So i double-checked on disk usage analyzer and my windows vista and it said that i have 121.9 gb left. I can't download anything over 8 gb. Can anyone Help????

---

### Post by linuxwin2 on 2011-10-28
Cat the output of
```
$df -h

```

---

### Post by raphaelb96 on 2011-10-29
> **linuxwin2 said:**
> Cat the output of
```
$df -h

```
this what i got
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  7.7G  7.6G  51% /
none                  1.5G  328K  1.5G   1% /dev
none                  1.5G  244K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda2             225G  112G  114G  50% /host
/dev/sdb1             299G   91G  208G  31% /media/My Passport

---

