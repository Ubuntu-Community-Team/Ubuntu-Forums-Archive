---
title: "Kernel upgrade process misunderstanding"
date: 2010-04-18
forum: General Help
---

### Post by Aikidoka69 on 2010-04-18
Everything I see states that you simply do apt-get install <new kernel> and reboot.  I'm trying that process with linux-image-virtual.  However, after running apt-get install linux-image-virtual I still only see generic-pae kernels in /boot.  I was under the impression I would now see new "-virtual" kernel images there.  This is 10.04 beta 2 x86.

---

### Post by Aikidoka69 on 2010-04-18
Ok, using dpkg to look inside the package I see that all files are in the generic-pae directories.  I thought that each would be separate even within a kernel revision.  For instance I could boot the generic-pae, server, or virtual versions of say kernel 2.6.32-22.  I also looked inside linux-image-server and it seems to also use the same generic-pae directory.  It is actually that you can only switch between kernel revisions and not types, e.g. server, virtual, rt?

---

