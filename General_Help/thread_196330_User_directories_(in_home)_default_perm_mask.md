---
title: "User directories (in /home) default perm mask"
date: 2006-06-14
forum: General Help
---

### Post by podollb on 2006-06-14
How do I change the default permission mask that is used when a new user is added to the system? Specifically his/her directory under /home. I would like all directories under /home to be masked to 700 automatically...

---

### Post by mexlinux on 2006-08-15
I need the same thing....
any ideas?

---

### Post by jeffathehutt on 2006-08-15
Edit the /etc/adduser.conf file:
```
gksudo gedit /etc/adduser.conf
```

Change DIR_MODE=0755 to whatever mask you want.

---

