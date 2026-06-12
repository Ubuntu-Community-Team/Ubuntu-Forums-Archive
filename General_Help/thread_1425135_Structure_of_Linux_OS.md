---
title: "Structure of Linux OS"
date: 2010-03-08
forum: General Help
---

### Post by cbou84 on 2010-03-08
Hello,
As far as I understood the construction of "Linux computer" can be accomplished in 5 parts:
- hardware
- kernel
- libraries
- GNU System tools
- software

If I compare that with Java, I think "GNU System tools" would be "JDK" and "libraries" would be the so called "API", right ??

* GNU System tools (compiler, editor, shell..)
* libraries (packages?? drivers??)

So, I may say KDE, GNOME and X Window-based interfaces are all part of "GNU System tools"? And both software and system tools are using "libraries" to communicate with the "kernel"?

Thanks

---

### Post by blueridgedog on 2010-03-08
This may help:

[http://www.gnu.org/](http://www.gnu.org/)

and

[http://www.gnu.org/gnu/gnu-linux-faq.html](http://www.gnu.org/gnu/gnu-linux-faq.html)

The GNU tools are simply software and libraries.

There is a great story about the coming together of the GNU tools/libraries/software and the Linux kernel to make a fully functional OS.  Today, that has been augmented by so many other contributions (Gnome, KDE, OpenOffice to name a few) that the concept of what is Linux is really a mix.

---

### Post by cbou84 on 2010-03-09
> **blueridgedog said:**
> 
[..] that the concept of what is Linux is really a mix.
Yes, indeed. That is the reason why I thought about starting this thread.

---

### Post by dcstar on 2010-03-09
> **blueridgedog said:**
> 
........
The GNU tools are simply software and libraries.
........

"Libraries" are simply software modules that are available for other software to use.

Application use libraries, system processes use libraries, other libraries use libraries.

All "libraries" essentially do is allow people to use code that already exists and not have to "reinvent the wheel" when they want some software to perform a purpose.

---

