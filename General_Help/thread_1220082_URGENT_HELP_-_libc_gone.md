---
title: "URGENT HELP - libc gone"
date: 2009-07-22
forum: General Help
---

### Post by vbtemp on 2009-07-22
while trying to upgrade libc versions, i removed the link libc.so.6.

The link still exists, it's just called libc.so.6-old

Now nothing works, e.g.,


[root@xxxx lib]# ls
ls: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory


Is there any way to recover while I'm still connected through the current ssh session?  If not this is a DISASTER

THANKS!!

---

