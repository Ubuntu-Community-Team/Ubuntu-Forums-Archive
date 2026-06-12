---
title: "Creative  X-Fi not showing in 2.6.35"
date: 2010-06-12
forum: General Help
---

### Post by KhaaL on 2010-06-12
I've been suffering a long time from [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=12309") and was quite happy to finally being able to use linux with the latest RC kernel 2.6.35. being lazy as i am, i got it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and installed it. Now however, while i got decent I/O throughput, my soundcard Creative X-Fi ceased to exist. I can't see that its support was stripped out of the kernel. How can i get my music back? :D

---

### Post by hansum_rahul on 2010-06-12
I have got the X-Fi and AFAIK, ALSA drivers are not available

You have to use OSS. Goto 4front website and download OSS. See the OSS wiki for problems faced by gstreamer and ALSA apps.

---

### Post by KhaaL on 2010-06-12
> **hansum_rahul said:**
> I have got the X-Fi and AFAIK, ALSA drivers are not available

You have to use OSS. Goto 4front website and download OSS. See the OSS wiki for problems faced by gstreamer and ALSA apps.

ALSA drivers not avaible in the .35 kernel or do you mean in general? because i'm running the 2.6.32 kernel that comes with the installation and X-Fi is working fine there.

---

### Post by KhaaL on 2010-06-13
OK, i just turned on the onboard audio and still no sound. According to my motherboard specification, its a "Onboard audio" with "Built-in High Definition 8 channel audio and "ALC888 CODEC".

Can someone please give me some insight if 2.6.35 has regressions regarding sound?

---

