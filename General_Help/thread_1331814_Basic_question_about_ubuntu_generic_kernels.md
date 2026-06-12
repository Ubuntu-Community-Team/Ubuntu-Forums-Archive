---
title: "Basic question about ubuntu generic kernels?"
date: 2009-11-19
forum: General Help
---

### Post by balteo on 2009-11-19
Hello,
Can anyone please tell me what **generic** mean in the context of ubuntu kernels?
Why can't I retrieve the kernel sources for a "**generic**" ubuntu kernel?
Thanks,
Julien.

---

### Post by seeker5528 on 2009-11-19
Generic means it is compiled to work with systems using x86/x86-64 compatible processors, without regard to whether they are AMD/Intel, Single core/Multiple core, or whether you have multiple CPUs.

There is a linux source package with the Ubuntu patches if you want to compile the kernel with the options you choose.

If you just want to compile something for your installed kernel, then install the matching headers package.  

If you want to compile the kernel yourself, but use the configuration of the installed kernel as a starting point either because you just want to change a few options or you need to patch the kernel, there are config files in the /boot directory that match the installed kernel, 'config-2.6.31-14-generic' for example, there is a 'make oldconfig' option that will create a new config file based on the existing one.

[http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html#upgrading](http://www.faqs.org/docs/Linux-HOWTO/Kernel-HOWTO.html#upgrading)

Later, Seeker

---

### Post by balteo on 2009-11-20
seeker5528,
thanks for your comprehensive reply!
J.

---

