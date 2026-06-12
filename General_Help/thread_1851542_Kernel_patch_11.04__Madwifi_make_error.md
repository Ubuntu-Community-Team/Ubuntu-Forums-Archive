---
title: "Kernel patch 11.04 : Madwifi make error"
date: 2011-09-28
forum: General Help
---

### Post by ac90b671 on 2011-09-28
I'm trying to get the madwifi drivers installed for my ath9k wifi card.
When I go to "make" the drivers, I get this error:

make
```

./kernelversion.c:14:34: fatal error: generated/utsrelease.h: No such file or directory
compilation terminated.
Makefile.inc:81: *** Cannot detect kernel version - please check compiler and KERNELPATH.  Stop.

```

Some useful stuff I can think of:

uname -r 
```
2.6.38-11-generic-pae
```
 
apt-get install linux-headers-generic-pae
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic-pae is already the newest version.

```

I'm not sure why make won't work. I'd really like to compile this patch. Any help would be greatly appreciated

---

