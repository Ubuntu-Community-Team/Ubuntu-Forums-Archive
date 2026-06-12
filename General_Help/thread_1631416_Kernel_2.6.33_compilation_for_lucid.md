---
title: "Kernel 2.6.33 compilation for lucid"
date: 2010-11-26
forum: General Help
---

### Post by Markus Zimmermann on 2010-11-26
Hi,

i'm unable to compile a kernel 2.6.33 via git for lucid following this howto:

[http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/)

The step debian/rules editconfigs stops after running the first flavor. I am not asked for further flavours included my own. Does anybody know how to workaround this? I need a kernel 2.6.33 for the DRM-Driver of my via-graphics-chip.

I suceeded compiling a kernel 2.6.35. So I am on my wits end.

Thank you, Markus

---

### Post by andrewthomas on 2010-11-26
Probably because there never was a lucid 2.6.33 kernel. 

 Why would you want to use a 2.6.33 kernel as opposed to a 2.6.35 kernel?

---

### Post by Markus Zimmermann on 2010-11-27
Because i need to compile a DRM-dirver vor a VIA CN896 chipset, which in my opinion only compile against a 2.6.33 kernel.

Markus

---

### Post by andrewthomas on 2010-11-27
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.7.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.33.7.tar.bz2)

---

