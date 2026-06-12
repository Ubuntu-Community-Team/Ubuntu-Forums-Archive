---
title: "Questions about kernel compilation"
date: 2011-01-23
forum: General Help
---

### Post by Fanatico on 2011-01-23
I am trying to rebuild latest version of Ubuntu kernel following the instructions from Kernel Compile Documentation page:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

So I have two questions:

1. In the "Modify the source for your needs" section of that page, it suggest

debian/scripts/misc/oldconfig ARCH

However there is NO oldconfig script file in debian/scripts/misc directory? can anyone suggest how to proceed?

2. Why does it suggest to use script files to build Ubuntu kernel, like "debian/rules", for example:

fakeroot debian/rules clean

I used to build kernels with simple make command.

Thanks

---

