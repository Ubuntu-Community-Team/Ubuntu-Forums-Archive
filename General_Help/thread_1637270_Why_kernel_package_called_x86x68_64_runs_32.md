---
title: "Why kernel package called x86/x68_64 runs 32"
date: 2010-12-04
forum: General Help
---

### Post by Claudio Pascual on 2010-12-04
Hello my friends,
   I am a bit confused. My system is running on 32 bit mode, but the kernel package info says the following:

# dpkg -l linux-image-2.6.32-26-generic
ii  linux-image-2.6.32-26-generic                            2.6.32-26.47                                      Linux kernel image for version 2.6.32 on x86/x86_64

   Is the same package able to run on both modes 32 and 64 bits?

   I couldn't find the answer anywhere.

---

### Post by Frogs Hair on 2010-12-04
Take a look at this , It's old but still valid. Go to help on the Firefox menu and look at about it will display what version you are running , 32 or 64. .[http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)

---

### Post by Claudio Pascual on 2010-12-04
Thanks very much Frogs Hair,
   I appreciate your help, but I think your link doesn't answer my question, which I understand is a weird one. It must be just a matter of naming conventions for the ubuntu packages' descriptions. 
   The description of the package says "x86/x68_64" but cannot be both at the same time, so I presume the actual system mode, wether 32 or 64 bits relies on utter configuration. I don't really know.
   Cheers mate,

Claudio

> **Frogs Hair said:**
> Take a look at this , It's old but still valid. Go to help on the Firefox menu and look at about it will display what version you are running , 32 or 64. .[http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/](http://ubuntu-tutorials.com/2007/01/27/how-to-find-your-ubuntu-or-kernel-version/)

---

