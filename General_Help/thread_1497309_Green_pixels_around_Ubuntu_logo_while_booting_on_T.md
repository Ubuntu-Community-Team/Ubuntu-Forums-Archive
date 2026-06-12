---
title: "Green pixels around Ubuntu logo while booting on Thinkpad T40"
date: 2010-05-30
forum: General Help
---

### Post by yukonho on 2010-05-30
System info:
Thinkpad T40 (2373 series)
1.5 GHz Pentium M
32 MB ATI Mobility Radeon 7500
Resolution 1024x768
1280 MB RAM

When booting and shutting down from the live CD, the Ubuntu logo has these odd green pixels around the logo and text edges - please see the attached image. Notice that the distortion is also around the text. However, the very last image before entering the desktop (logo and full 5 markers) looks normal. What's causing this? I'm wary of installing if it's evidence of a larger video incompatibility. Any suggestions for a fix? It looks like it's loading the radeon module (which has worked fine in the past). The desktop appears fine as well. 

I had the same issue when trying to boot the Netbook Edition on my laptop.

Thanks!

---

### Post by dino99 on 2010-05-30
load it with nomodeset on the boot line

---

### Post by gson on 2010-10-11
Looks like [bug #656848]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/656848/")

---

