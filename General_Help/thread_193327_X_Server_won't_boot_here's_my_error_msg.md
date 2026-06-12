---
title: "X Server won't boot here's my error msg:"
date: 2006-06-09
forum: General Help
---

### Post by LsrLine on 2006-06-09
I get the following:
```
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

Fatal server error:
No GLX modules loaded
dlopen: /usr/lib/xorg/modules/xgl/libglx.so: cannot open shared object file: No such file or directory

FatalError re=entered, aborting
No GLX modules loaded

```

Plus I don't have any internet connection in the console.  How can I fix my x server?

Thanks Guys!

---

### Post by pyromithrandir on 2006-06-09
It would help us troubleshoot if you could post your xorg.conf file.

---

### Post by encompass on 2006-09-14
Looks like you were trying to install glx... restore your original gdm.conf-custom file and it should get you back in... I just did it with that error.

---

