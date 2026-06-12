---
title: "Nautilus crashing constantly after recent update"
date: 2011-02-11
forum: General Help
---

### Post by manustays on 2011-02-11
After a recent update a week back or so, the nautilus is crashing very often. I have noticed it mostly happens while closing a nautilus window or maybe sometimes while trying rename a folder, etc.

The kernel log says:

Feb 11 12:25:58 PC kernel: [113047.344460] nautilus[31254]: segfault at 506 ip 00cba0d0 sp bfb895e0 error 4 in libgobject-2.0.so.0.2600.0[c91000+40000]

The nautilus is restarted after the crash. Tried searching the error msg on google but couldn't find anything :(

---

### Post by manustays on 2011-02-11
Got a new error-msg in kernel log after a recent crash:


Feb 11 20:03:10 PC kernel: [140432.813619] nautilus[536]: segfault at 0 ip 010f9ef9 sp bfc85100 error 4 in libgtk-x11-2.0.so.0.2200.0[e98000+3c8000]

Guys plz help :(

---

