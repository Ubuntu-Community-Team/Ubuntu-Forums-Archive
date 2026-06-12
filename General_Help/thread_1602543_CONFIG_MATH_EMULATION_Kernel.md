---
title: "CONFIG_MATH_EMULATION Kernel"
date: 2010-10-21
forum: General Help
---

### Post by rbrahman on 2010-10-21
When I am running the OpenSSL FIPS Version 1.2 on Ubuntu, it is giving 
an "Illegal instruction" error on certain crytographic functions esp RSA Keys.  

I am running on Amazon eC2 Using Ubuntu Jaunty.
 
It turns out that the illegal instruction was Ubuntu, the  underlying PPC processor on eC2 must not have Floating Point Units.

I need to know how to turn on CONFIG_MATH_EMULATION for fpu emulation in Ubuntu. 
I am sure there is a config file somehwere to change this, but I have no idea where it is.

Will this require a re-compile the kernel?

I haven;t been this deep into linux, in fact building the FIPS 
was the first time I have done config, make, install in a while thanks to Ubuntu :)

---

### Post by srs5694 on 2010-10-22
That option is a kernel compile-time option. If the Ubuntu kernel doesn't include it, you'll have to reconfigure and recompile your kernel to get it. [This page](http://cateee.net/lkddb/web-lkddb/MATH_EMULATION.html) provides some basic information.

---

