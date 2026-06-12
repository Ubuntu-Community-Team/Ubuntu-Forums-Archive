---
title: "Flash problem?"
date: 2012-01-19
forum: General Help
---

### Post by joesnose on 2012-01-19
hello all,

just wondered if anyone could shed some light on why flash video is so poor on ubuntu. I do really like the idea of ubuntu, open source, completely customisable, etc. I just dont understand why when i play flash videos they stutter and jerk and look unwatchable, while on the same machine windows runs the same videos as smooth as silk!

what gives? i am using an intel onboard 915 graphics card, a little underpowered perhaps, but seemingly not a problem for windows. It is getting on my nerves a little, so much so i think i shall have to reinstall windows! horrible.

---

### Post by dragonfly41 on 2012-01-19
You might try installing Flash-Aid 2.2.2 as Firefox add on.

[http://www.webgapps.org/add-ons/flash-aid](http://www.webgapps.org/add-ons/flash-aid)

---

### Post by snowpine on 2012-01-19
A good first step is to verify that your system meets [the minimum hardware requirements for the Flash plugin]("http://www.adobe.com/products/flashplayer/tech-specs.html"):

> Linux

    2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
    Red Hat® Enterprise Linux (RHEL) 5.6 or later (32-bit and 64-bit), openSUSE® 11.3 or later (32-bit and 64-bit), Ubuntu 10.04 or later (32-bit and 64-bit)
    Mozilla Firefox 4.0 or Google Chrome
    512MB of RAM; 128MB of graphics memory

Based on your post, it sounds like you are lacking the 128mb of graphics memory. If so (and you meet all the other requirements) then a video card update is the single best hardware upgrade you can make for watching Flash.

You are correct that the hardware requirements are higher in Linux than Windows. Since Flash is proprietary "closed source" software, only Adobe Corp can address this problem.

A temporary workaround that I highly recommend is to simply not use the Flash plugin. You can get browser plugins for VLC or Totem, or you can download the video and watch it from your hard drive with your favorite media player. :)

---

