---
title: "Odd nautilus bug in Jaunty"
date: 2010-02-07
forum: General Help
---

### Post by Togezo on 2010-02-07
I have this very odd little problem with nautilus; if I have files in the wastebasket, and I try to view its contents, then what happens is nautilus opens a window, and then crashes. Syslog and messages both get this output:

(This example is from when I re-created the bug 3 times)
Feb  7 10:00:54 padraic-laptop kernel: [  780.057995] nautilus[3620]: segfault at b79ecbe0 ip b77b32cb sp bfa7fbc0 error 7 in libglib-2.0.so.0.2200.3[b7753000+b8000]
Feb  7 10:00:58 padraic-laptop kernel: [  783.844906] nautilus[5176]: segfault at 63657845 ip b792476b sp bf9e2130 error 4 in libglib-2.0.so.0.2200.3[b78ca000+b8000]
Feb  7 10:01:14 padraic-laptop kernel: [  799.720984] nautilus[5188]: segfault at 1 ip b78c976b sp bf8f97c0 error 4 in libglib-2.0.so.0.2200.3[b786f000+b8000]

As a bit more information; my system is 1686, Ubuntu 9.04, 2.6.28-18-generic #59-ubuntu, and using GNOME Nautilus 2.26.2

---

