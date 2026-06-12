---
title: "Computer Janitor, Ubuntu Software Center, and Update Manager all close after starting"
date: 2010-01-07
forum: General Help
---

### Post by jhenager on 2010-01-07
I just went to run Computer Janitor, and it started to load, then the tab disappeared. I restarted to see if that might be it. Then went to the Software Center to see if there was something else that might do the same thing, and IT did the same thing as Computer Janitor. So I went to check for any updates, and IT does the same thing as well.
It looks like it is loading, and then the window just closes. No error messages or anything.
Very strange. Any advice?

Karmic on a Pentium 4 EE chip on an Intel motherboard. More details if you need them.

80 error 7 in libapt-pkg-libc6.10-6.so.4.8.1[a61000+bd000]
[  100.751776] software-center[2004]: segfault at 196f844d ip 029d8105 sp bfca8780 error 6 in libapt-pkg-libc6.10-6.so.4.8.1[29a0000+bd000]
[  165.626572] update-manager[2177]: segfault at 1958a2bd ip 05ebd105 sp bfcdbf60 error 6 in libapt-pkg-libc6.10-6.so.4.8.1[5e85000+bd000]
[  346.998563] computer-janito[2296]: segfault at c6686955 ip 0030c105 sp bfafb6b0 error 7 in libapt-pkg-libc6.10-6.so.4.8.1[2d4000+bd000]

---

### Post by philinux on 2010-01-07
Try running from the terminal

```
update-manager
```

Report back with any errors.

---

### Post by jhenager on 2010-01-07
jeff@jeff-desktop:~$ update-manager
Segmentation fault

Thanks for the quick reply.

---

### Post by philinux on 2010-01-07
> **jhenager said:**
> jeff@jeff-desktop:~$ update-manager
Segmentation fault

Thanks for the quick reply.

[http://ubuntuforums.org/showthread.php?t=803215](http://ubuntuforums.org/showthread.php?t=803215)

---

### Post by jhenager on 2010-01-08
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=803215](http://ubuntuforums.org/showthread.php?t=803215)

That fixed the issue. I appreciate it.

---

