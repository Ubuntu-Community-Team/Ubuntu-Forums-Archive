---
title: "Need 32-bit libraries to install ifort"
date: 2010-06-08
forum: General Help
---

### Post by abgemacht on 2010-06-08
Hello,

I am running the AMD64 version of Ubuntu 10.04.  I am trying to install the Intel Fortran Compiler 11.1.072.  Before the install, it says I'm missing the following 32-bit compatible libraries:
libstdc++
libstdc++5
glibc
libgcc

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=497745"), but I'm getting the same message.

Any help would be appreciated.

---

### Post by _khAttAm_ on 2010-06-08
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by jerome1232 on 2010-06-08
Have you tried getlibs?

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

It's always been able to figure out dependencies for me in the past.

Is it possible that your program is looking for dependencies in the wrong spot? I know some distro's put 32 bit libraries in /lib and 64 bit libraries in /lib64 where as Ubuntu 64 bit put's 64 bit libs in /lib and 32 bit ones in /lib32. With /lib64 being a symnlink to /lib. 

So it might be looking for it's 32 bit libraries in /lib when they are in /lib32.

---

### Post by abgemacht on 2010-06-08
It seems that this is a known issue with the latest version of ifort.

I ended up finding the answer [here]("http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/") in case anyone else has the problem.

Thanks for your help.

---

