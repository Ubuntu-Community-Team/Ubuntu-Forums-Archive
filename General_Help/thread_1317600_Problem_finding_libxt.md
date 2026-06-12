---
title: "Problem finding libxt"
date: 2009-11-06
forum: General Help
---

### Post by rozen on 2009-11-06
Hi,

I have recently installed Ubuntu 9.10 and I like it a lot.  But I have an old program that I really like and I am trying to build it from the source.  However, the code depends on libgtk-1.2 which I am unable to find using synaptic. So I decided to try building gtk+1.2. However, that package includes  <X11/Intrinsic.h> which seems to be missing. When I do a Google search on X11/Intrinsic.h it tells me that it is in the debian package libxt.  I cannot find the package libxt using synaptic.  I would really appreciate any suggestion as to where I might obtain the package or another package or how else I might keep going.

Thanks in Advance,
Don

---

### Post by michy99 on 2009-11-06
X11/Intrinsic.h is included in libxt-dev.

---

### Post by rozen on 2009-11-06
Thank you very much.  I was able to compile my program.

---

### Post by michy99 on 2009-11-06
Glad it worked. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) is a great resource to find what package contains a file or vice versa.

---

