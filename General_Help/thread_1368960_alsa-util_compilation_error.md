---
title: "alsa-util compilation error"
date: 2009-12-31
forum: General Help
---

### Post by shariefbe on 2009-12-31
when i try to compile alsa-util for my arm processor i am getting the following error
```

checking for arm-none-linux-gnueabi-gcc option to accept ISO C89... (cached) none needed
checking dependency style of arm-none-linux-gnueabi-gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin//install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS... -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
Configuration of glib library has failed
sharief@sharief-desktop:/mnt/freescale/sources/alsa-utils-1.0.22$ 
```

can any one help me to rectify this error

---

### Post by Zoot7 on 2010-01-07
You need to install **libasound-dev.**

Entering this in the terminal should pull in all the build dependencies for you.
```
sudo apt-get build alsa-utils
```

---

