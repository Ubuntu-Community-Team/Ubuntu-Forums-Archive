---
title: "Running multiple versions of glibc"
date: 2009-10-22
forum: General Help
---

### Post by ragtag on 2009-10-22
Hi,

  I'm trying to run a program that depends on an older version of libc. I have an install of CentOS with libc-2.5.so, where the program runs without errors.

  What I've got so far:

  ldd returns this:
```

  linux-vdso.so.1
  libX11.so.6
x libxml2.so.2     
x  libGL.so.1      
x  libGLU.so.1     
  libXmu.so.6
x  libz.so.1       
  libdl.so.2
  libpthread.so.0
  libm.so.6
x  libstdc++.so.6  
  libgcc_s.so.1
  libc.so.6
o  libxcb.so.1  <- Only exists on Ubuntu....missing from CentOS????
x  libGLcore.so.1       
x  libnvidia-tls.so.1   
  libXext.so.6
  libXt.so.6
  libSM.so.6
  libICE.so.6
  /lib64/ld-linux-x86-64.so.2
  libXau.so.6
  libXdmcp.so.6
  libuuid.so.1

```

 The libraries marked wit x have a different minor version on CentOS 5.3 and Ubuntu 9.04. I've tried copying them to a lib folder of their own, and using $LD_LIBRARY_PATH to point to them. This worked fine for everything except the libGL* and libnvidia...but I'm pretty sure they are not causing the error, so I've just left them out. But I'm still getting the same error in the program.

 My guess it's the next level of dependencies, which is libc. Is there any way I can run this program, with an older version of libc?

 I've tried a number of things (copying the old libc and ld-linux...over and more), but nothing has worked so far. Any ideas?

 If I can't figure this out I'll have to run CentOS instead of Ubuntu, which will feel a bit like going back to the 80's!
:guitar:

---

### Post by Giblet5 on 2009-10-22
You are digging yourself into a hole from which you might not escape w/o a reinstall. What you're trying to do is OK for someone who knows enough not to even try it. (Yes, that IS a paradox)

Either install the software that you want to use from the repositories or rebuild from the source code.

If you don't, you will reinstall eventually.

If you want a program that can be copied from CentOS to Ubuntu and pretty-much just *work*, rebuild it from source and use static linkage.

---

### Post by ragtag on 2009-10-22
Rebuilding from source is unfortunately not an option, as the source is not available (commercial software). :(

---

