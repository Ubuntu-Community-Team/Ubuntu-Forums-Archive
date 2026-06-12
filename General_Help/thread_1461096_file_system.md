---
title: "file system"
date: 2010-04-23
forum: General Help
---

### Post by thundaraptor on 2010-04-23
I can't write to directories inside my main file system.  This is annoying, how to change?

---

### Post by sisco311 on 2010-04-23
Please elaborate, what are you trying to do?

---

### Post by thundaraptor on 2010-04-24
basic file maintenace, creating directories, storing things outside of my home directory.  i was trying to write a file inside an extension of the etc dir so that I could better control my mouse but otherwise, I can't read/write inside the file system.  is that something of a cmod situation?

---

### Post by ubername on 2010-04-24
You are not supposed to be able to write to directories other than in your home folder. If you need to, you need to do it as super user /root / however else you want to describe it.

One way of doing this is to run

```
gksu nautilus
```

but do so at your peril - there is good reason for protecting these files.

---

