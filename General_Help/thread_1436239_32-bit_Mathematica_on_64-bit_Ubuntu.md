---
title: "32-bit Mathematica on 64-bit Ubuntu"
date: 2010-03-22
forum: General Help
---

### Post by nmsbaeta on 2010-03-22
Hello!

I have a 64-bit computer (MacBook6,1) running the 64-bit version of Ubuntu 9.10.

Unfortunately I have to install a 32-bit (closed source) application, Mathematica 7 (I know there is a 64-bit version of Mathematica, but I only have a license for the 32-bit version).

I presume that I'll be having problems installing Mathematica - eventually I will be unable to do it :-(  So, before trying to install Mathematica, is there any thing I should do?

Has anyone tried to do something similar?

TIA!

---

### Post by patchwork on 2010-03-22
Although I haven't had any experience with Mathematica, I have been able to install 32 bit programs on 64 bit Ubuntu.  Typically, this involves checking the dependencies with ldd, installing the necessary 32 bit libraries, and linking libraries as needed.  Unfortunately, without having the program in front of me, I don't know how useful I can be with this...

---

