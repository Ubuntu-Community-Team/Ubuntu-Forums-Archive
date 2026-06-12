---
title: "intel compilers 11.1 installation problem"
date: 2009-11-30
forum: General Help
---

### Post by slyi on 2009-11-30
Hi All, 

I can not install the current version of Intel Compilers. 

Intel compiler version: 11.1.059
Ubuntu versions failing: 9.04 and 9.10
System: x86_64

Note that Ubuntu 9.04 is officially supported by Intel on 64bit systems (I am asking this question on Intel support as well and will post if a resolution comes up). 

According to the Intel installer the problem is:

```

32-bit libraries not found on this system.
This product release requires the presence of 32-bit compatibility libraries
when running on Intel(R) 64 architecture systems. One or more of these libraries
could not be found:
    libstdc++
    libstdc++5
    glibc
    libgcc
Without these libraries, the compiler will not function properly.  

```

I tried installing (via aptitude on Jaunty, dpkg on Karmic) [libstdc++5 from Jaunty]("http://packages.ubuntu.com/jaunty/libs/libstdc++5") but that didn't change anything (exact same complaint at install). 

Packages lib32gcc1 and lib32stdc++6 were already installed. 

Any ideas? 

Thanks,
slyi

---

