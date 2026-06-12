---
title: "File permissions. Not owner of drive"
date: 2011-03-31
forum: General Help
---

### Post by kinns1 on 2011-03-31
So my girlfriend's macbook hard drive is failing. I have gotten it mounted in ubuntu, and can access the file system, but when I try to back stuff up, it wont let me because I don't have permission to access the folders. What can I do to force permissions to allow me to backup her data?

---

### Post by TeoBigusGeekus on 2011-03-31
Try with
```
gksu nautilus
```

---

### Post by vanadium on 2011-03-31
As root, you will have access. Be very careful, though.

Open a nautilus windows with root privileges with the command "gksudo nautilus". With this window, you will have full access to the mounted drive, but also have full access to write anywhere in your system. So that is why you must be careful. Copy the data you need to safeguard, then close that nautilus window.

---

