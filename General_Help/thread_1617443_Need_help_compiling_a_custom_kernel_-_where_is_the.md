---
title: "Need help compiling a custom kernel - where is the debian.master folder?"
date: 2010-11-09
forum: General Help
---

### Post by Bliepo32 on 2010-11-09
Hello everyone,

I am currently trying to compile my own custom Ubuntu kernel, mainly for learning purposes and because the current one is crashing a lot. I am using this how to to compile the kernel: [How to compile a Ubuntu 10.10 (Maverick) kernel](http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/).
I am stuck at the step of creating a new config. It tells me to copy a config file from the debian.master folder, but it is not present. Has this moved somewhere else or what happened?

---

### Post by iponeverything on 2010-11-09
look for the config in /boot

copy the one over to the source directory that you need and rename it to .config -- then run menuconfig save and exit.

---

### Post by Bliepo32 on 2010-11-09
Thanks for your quick reply. I will try doing that and see how things go.

EDIT: Now the debian.master folder suddenly appeared (after recloning), so I guess I am good to go.

---

