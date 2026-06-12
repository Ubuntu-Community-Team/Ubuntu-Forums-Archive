---
title: "deb files"
date: 2010-06-02
forum: General Help
---

### Post by genux05 on 2010-06-02
Hi all,

Was wondering if there was a special way to create deb files for kubuntu ? 

I would like to package up a couple of c++/java/c# applications into deb files.

Thanks very much.

---

### Post by Locke_99GS on 2010-06-02
deb files for Kubuntu are the same as for Ubuntu. There is no special way to create them, any of the hundreds of packaging tools will work.

I use dpkg-buildpackage, because I'm lazy and it works. 

For things that do not need compiling (such as shell scripts, for instance) you could use "epm", also pretty simple to use.

---

