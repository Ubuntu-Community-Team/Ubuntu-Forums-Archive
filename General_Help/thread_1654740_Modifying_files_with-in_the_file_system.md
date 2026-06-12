---
title: "Modifying files with-in the file system"
date: 2010-12-28
forum: General Help
---

### Post by IanKaminski on 2010-12-28
Hello, I'm having difficulty installing a MOD for Lpanzer because I can not modify any files in the file system because I'm not the owner. According to permissions Root is the owner. So how do I either tell Ubuntu I'm the owner? Or do I need a utility program to get things going?

---

### Post by anystupidname1 on 2010-12-28
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by IanKaminski on 2010-12-29
Ok, it worked, took some doing but I got it, thanks.

---

### Post by anystupidname1 on 2010-12-29
That was kind of a two-part question and I only gave you one answer. So, for future reference, you CAN change permissions and ownership on files. It may be a bad idea depending on where the files are and their purpose. So use them like you would a loaded gun.

From a terminal, type:
```
man chown
man chmod
```

---

