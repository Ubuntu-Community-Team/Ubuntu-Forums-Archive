---
title: "linux-headers-generic - VITAL?"
date: 2010-11-25
forum: General Help
---

### Post by madmax.santana on 2010-11-25
What would happen if I remove (accidentally) ```
linux-headers-2.6.35.23
``` and ```
linux-headers-2.6.35.23-generic
``` and ```
linux-headers-generic
``` from my system?

---

### Post by Gunman1982 on 2010-11-25
Shouldn't be a problem since they are only used to build modules or programmes which rely on the kernel headers.

---

### Post by WorMzy on 2010-11-25
Read this: [What Are Kernel Headers]("http://www.serverschool.com/operating-systems/what-are-kernel-headers/")

You don't need them for Ubuntu to work, but you might need them for compiling kernel modules.

---

