---
title: "Intel fortran installation woes"
date: 2010-02-05
forum: General Help
---

### Post by ranndal on 2010-02-05
Hi you all,

a newbie here, as will be evident below. (Initially I posted this in the wrong forum and this is probably the wrong one too...)

I tried to install intel fortran. After failing, I followed the detailed advice on the forums, e.g. [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571) and [http://ubuntuforums.org/showthread.p...l+Fortran+11.0]("http://ubuntuforums.org/showthread.php?t=1082782&highlight=Install+Intel+Fortran+11.0")

This initially looked promising, but when I run install.h with "sudo", the way it says to run it, I am still getting the very same error message when installing, namely:
+++++++++++++++++++++++++++++

This product release requires the presence of 32-bit compatibility libraries
when running on Intel(R) 64 architecture systems. One or more of these libraries
could not be found:
    libstdc++
    libstdc++5
    glibc
    libgcc
Without these libraries, the compiler will not function properly.  Please refer 
to Release Notes for more information.

++++++++++++++++++++++++++++++++

:mad:I am a newbie, but I suspect part of the problem is that the installer is not putting things where everyone says it will go, namely in "opt" --but, to be honest I have no idea where it is going. I initially tried to install without sudo, and it put things, I guess, into my home user directory. (And ... why shouldn't it work there, anyway? never mind. also why should 64-bit intel require 32 bit libraries? never mind.) But doing it over, according to the thread instructions, should -- I thought -- have taken care of that. 

I could not cut and paste files into various locations because I am not the "owner," even though I most certainly AM!!!! the owner of my computer, darn it. (Does this terminology seem odd to anyone else?)

I am considering activating "root" and installing it as the "superuser," but the dire warnings are holding me back.

Anyway, thanks for your help.

---

### Post by gmargo on 2010-02-06
> why should 64-bit intel require 32 bit libraries? The fortran compiler is a probably 32-bit application, or else maybe it can build 32-bit applications. The 32-bit compatibility libraries are all named with a leading "lib32".  Here are Karmic lib32 packages: [http://packages.ubuntu.com/search?keywords=lib32&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=lib32&searchon=names&suite=karmic&section=all)

---

### Post by ranndal on 2010-02-08
the answer is here:
[http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

---

