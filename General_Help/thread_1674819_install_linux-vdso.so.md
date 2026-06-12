---
title: "install linux-vdso.so"
date: 2011-01-24
forum: General Help
---

### Post by any.linux12 on 2011-01-24
Hi all!

Long time no threads :D

I need help to install the linux-vdso.so in my ubuntu 9.04 64bits. I need it because multiple applications that I have programmed need it due to an inclusion of a 3rd party software.
As I have seen this library is only available to fedora suse and other rpm OS. Should I install in my ubuntu machine? and how? I already tried to use the getlibs and tried to downloaded it but I didn't find it anywhere.

thank you.

---

### Post by lightningfox on 2011-01-24
Hi

You can use alien to convert rpms into debs.

[http://www.kabatology.com/03/15/how-to-convert-rpm-files-to-deb-files-with-alien/](http://www.kabatology.com/03/15/how-to-convert-rpm-files-to-deb-files-with-alien/)

---

### Post by hawkmage on 2011-01-24
The lib linux-vdso.so ( as well as linux-gate.so) is not going to be found.  It is a virtual Dynamically Shared Object and part of the kernel.  You may want to take a look at this: [http://www.trilithium.com/johan/2005/08/linux-gate/](http://www.trilithium.com/johan/2005/08/linux-gate/)

---

