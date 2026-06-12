---
title: "linux-crashdump not working with custom kernel"
date: 2011-11-16
forum: General Help
---

### Post by patch11 on 2011-11-16
Hello,

I have a custom kernel running on my ubuntu 11.10. Currently my kernel crashes sometimes, so I installed "linux-crashdump".


Unfortunately, when my system freezes, linux-crashdump doesn't seem to handle the kernel-panic.


What am I doing wrong?
Does linux-crashdump doesn't work with custom kernels?

Do I have to enabled the kexec and kexec-load services?


Thanks a lot,
Christoph

---

### Post by patch11 on 2011-11-16
Little update (if anybody is interested):

I managed now to get the crash-dump on a ubuntu-kernel.

I enabled the services apport, kexec and kexec-load (not sure if they are really needed) and installed makedumpfile-static.

I copied the makedumpfile-binaries as described here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733/comments/15)

With this, I get a crash-dump on a clean ubuntu-kernel. However, on my custom 3.0.9-kernel still not.

So, now I merge my custom kernel into the kernel from git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git .


I hope that I then get a crashdump.

---

