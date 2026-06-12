---
title: "changed kernels and now ATI drivers don't work"
date: 2011-02-06
forum: General Help
---

### Post by jmknsd on 2011-02-06
I updated my kernel on 10.04 using

```
sudo apt-get update && sudo apt-get install linux-image-generic-lts-backport-maverick linux-headers-generic-lts-backport-maverick
```

and now trim works, but jockey gave me an error about not being able to find the ATI driver. I downloaded the 11.1 driver(HD 4850 on 64 bit) from AMD and installed it. After reconfiguting xorg and rebooting many times, I cannot get any kind of hardware graphics aceeleration. I can't watch dvd quality video without stuttering, nor can I play any kind of game or glxgears.

Is there something else I need to be doing, or does the kernel/distro combination I have not allow for the proprietary driver? Also, I remember hearing that AMD had good open source drivers, are these the ones that are used by default, or do I need to go elsewhere to install them?

---

### Post by ajgreeny on 2011-02-06
I'm not too sure about your kernels or why you are using them, but I have to admit to having kernel 2.6.37-12 on my machine, (also 10.04), which I installed from the ubuntu kernel ppa repository.   I also have an ATI card, and thought this newer kernel might help with enabling KMS for better rendering.  I'm not sure if it really does help, but it certainly is OK on my old ATI 9200SE card, for which I use the open source ati/radeon driver, so that may be the difference between our systems that helps mine work OK.

Go to [https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa") for more info and if you want to try it out..

---

