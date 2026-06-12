---
title: "Slower boot since re-install"
date: 2010-11-16
forum: General Help
---

### Post by PaulHeywood on 2010-11-16
Hi there - I carelessly didn't apply a couple of updates correctly a few days ago which led me to reinstall Ubuntu 10.04 (thanks to a home partition it was all pretty painless).

But, since the reinstall the boot has gone from blindingly fast to average.

Has anyone any ideas about what would of caused this ?  It's a shame, the boot cycle was one of the outstanding highlights of Ubuntu,

Paul.

---

### Post by efflandt on 2010-11-16
The first thing you should do is check **dmesg | less** in a terminal and see where any significant lag is or if anything jumps out at you.  It is possible that you had a kernel boot parameter or some other configuration you forgot about or improved once you did normal updates or added special repositories.

---

### Post by PaulHeywood on 2010-11-16
Excellent advice, interestingly right at the bottom of dmesg is this :

```
[    9.672699] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   20.368022] eth0: no IPv6 routers present
```

.. which implies it's something to do with my display driver ?

---

