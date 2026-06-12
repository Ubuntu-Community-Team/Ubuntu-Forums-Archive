---
title: "Radeon  HD 58xx and Linux"
date: 2009-12-16
forum: General Help
---

### Post by Renée Jade on 2009-12-16
Hey all,

I'm building a PC and I'm in a bit of a pickle on the GPU front, since I want DirectX 11 support, but I need (well, sort of need) Linux. Has anybody tried the Radeon HD 5850 or 5870 under Linux? Did any of you get decent results under Ubuntu 9.10, Kubuntu 9.10, Slackware or Arch?

Thanks for any response. :)

---

### Post by ean5533 on 2009-12-16
> **Renée Jade said:**
> Hey all,

I'm building a PC and I'm in a bit of a pickle on the GPU front since, I want DirectX 11 support, but I need (well, sort of need) Linux. Has anybody tried the Radeon HD 5850 or 5870 under Linux. Did any of you get decent results under Ubuntu 9.10, Kubuntu 9.10, Slackware or Arch?

Thanks for any response. :)
I can guarantee that you'll get absolutely zero DirectX performance... because DirectX doesn't exist in Linux. :) Rendering in Linux is done with OpenGL.

I don't know how well those two cards specifically will work, but I do know that Radeon cards don't typically have amazing 3D performance on Linux compared to Nvidia cards; the drivers aren't that good yet.

Are you asking because you're a gamer, or is there something else you're doing with you graphics card(s)?

---

### Post by Renée Jade on 2009-12-16
> **ean5533 said:**
> I can guarantee that you'll get absolutely zero DirectX performance... because DirectX doesn't exist in Linux. :) Rendering in Linux is done with OpenGL.

Obviously. DirectX is a game programming API. People don't really write video games for Linux. There is this nifty thing called dual-booting though.

> I don't know how well those two cards specifically will work, but I do know that Radeon cards don't typically have amazing 3D performance on Linux compared to Nvidia cards; the drivers aren't that good yet.

Are you asking because you're a gamer, or is there something else you're doing with you graphics card(s)?

I'm building a gaming machine. But I use Linux for everything apart from games. So I need the thing to work with both. I know that a lot of work is being done to get ATI support in Linux up to scratch. This is why I need a testimonial. Guessing is leading me in circles. I need evidence.

Thanks for the reply.

---

### Post by 3rdalbum on 2009-12-16
According to a few posts [here]("http://www.phoronix.com/forums/showthread.php?t=19250&page=5"), the 5850/70 works with the Catalyst driver that shipped with Ubuntu 9.10. There is an "unsupported hardware" watermark though.

Apparently there is a new driver which may or may not still be in beta, that is available from ATI, that officially supports the 5000 series.

Basically, check out [www.ati.com](www.ati.com) and see the release notes for their latest drivers.

---

### Post by Renée Jade on 2009-12-16
> **3rdalbum said:**
> According to a few posts [here]("http://www.phoronix.com/forums/showthread.php?t=19250&page=5"), the 5850/70 works with the Catalyst driver that shipped with Ubuntu 9.10. There is an "unsupported hardware" watermark though.

Apparently there is a new driver which may or may not still be in beta, that is available from ATI, that officially supports the 5000 series.

Basically, check out [www.ati.com]("http://www.ati.com") and see the release notes for their latest drivers.


Thanks mate :D

I'm still very much open to testimonials. If I do buy one of these I will post a testimonial (and maybe some benchmarks) on the performance.

---

### Post by MaxIBoy on 2009-12-16
Phoronix has done benchmarks, and the HD5xxx series does not outperform the HD4xxx series on Linux **yet**, despite ATI having roughly doubled the specs. Driver improvements will come and the performance will improve.

---

### Post by Renée Jade on 2009-12-16
> **MaxIBoy said:**
> Phoronix has done benchmarks, and the HD5xxx series does not outperform the HD4xxx series on Linux **yet**, despite ATI having roughly doubled the specs. Driver improvements will come and the performance will improve.


Yeah it's really not a choice between HD4's and HD5's for me. It's a choice between HD5's or buying a cheaper Nvidia and then waiting for the GeForce 300s (or maybe even longer). Obviously the latter is not ideal. And I suppose if I'm going to buy a cheaper Nvidia then give it to my brother when I upgrade, I might as well buy the HD58xx and then buy a cheaper Nvidia specifically for Linux if the HD58 won't play nice. 

Thanks for the help guys.

---

### Post by MaxIBoy on 2009-12-17
Understood. You can see a linux-oriented review of the 57xx series here:
[http://www.phoronix.com/scan.php?page=article&item=amd_juniper&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_juniper&num=1)
And some extra benchmarks here:
[http://www.phoronix.com/scan.php?page=article&item=amd_juniper_scaling&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_juniper_scaling&num=1)

Of course you're getting a 58xx instead of a 57xx, but it's probably still useful material.

---

### Post by blackmonjd on 2010-12-03
Pretty late for the OP, but I have a 5850 working in linux.  Had to use the proprietary drivers for full functionality, and updating can be a little scary. Make sure to back up any current configurations, which should be done anyways, before ANY updates.
 
A good reference site for this card (and other ATI/AMD cards as well)
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
 
Run into a few issues though. Like after switching monitors there's a line at the top that doesn't show up properly.  Sometimes it fixes itself and sometimes not. Anybody else had this issue?

---

