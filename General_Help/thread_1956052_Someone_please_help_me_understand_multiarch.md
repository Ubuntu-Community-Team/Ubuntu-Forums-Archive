---
title: "Someone please help me understand multiarch"
date: 2012-04-10
forum: General Help
---

### Post by lykwydchykyn on 2012-04-10
For the last six months, I've been trying to figure out how multi-arch works on Ubuntu.  In the old days (pre-onieric), we installed a special i386 libs package on 64-bit and 32 bit software could be pointed to that.

Now, I have an entirely duplicated set of packages available designated i386.  I assume that when I install a 32 bit package, it will pull in its required dependencies from these i386 packages.

The problem is, i386 packages conflict with their amd64 counterparts.  Which means that if my 32 bit application has *any* dependencies whatsoever, it won't install.

For example, today I tried to install linberry, which was only packaged for i386.  It depends on libfuse, libglade, and a few other i386 packages.  Can't install those, because they conflict with the amd64 packages I already have.

So what's the point??  Why do I have i386 packages available if they can't be installed alongside amd64 packages?

---

