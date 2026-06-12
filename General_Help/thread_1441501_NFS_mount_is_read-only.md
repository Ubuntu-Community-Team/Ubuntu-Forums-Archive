---
title: "NFS mount is read-only"
date: 2010-03-28
forum: General Help
---

### Post by codeking on 2010-03-28
I've set up an NFS server on my MacBook, and mounted it on my Ubuntu desktop.  Everything works fine, except all the files are read-only.

/etc/exports on MacBook
```
/Users/theron/Sites 192.168.2.100/200(rw,no_root_squash,sync)
```

/etc/fstab on Ubuntu Desktop
```
Therons-MacBook.local:/Users/theron/Sites /media/MacBook  nfs  rw,auto 0 0
```

Any possible solutions?

---

### Post by codeking on 2010-03-29
Finally figured it out!

---

### Post by abhishek.kona on 2010-11-19
Could you post what was that you fixed.?

---

