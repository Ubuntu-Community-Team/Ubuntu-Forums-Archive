---
title: "Dual Monitor Madness"
date: 2012-05-18
forum: General Help
---

### Post by fallofshadows on 2012-05-18
Well, I bit the bullet and updated from 11.10 to 12.04 today. I need to remember that the newest version is NOT always the best, especially not with open source tech.

I finally got my wifi speeds back to normal, but I'm having issues with my dual monitor setup. When I plug in the VGA cable to the monitor (some old LCD TV that says "Hisense" on the front), both of my screens go black with my cursor frozen in space. When I try booting with the monitor attached, it boots to a black screen of death. Both require a hard reset.

Does anyone have any idea how to fix this? This is pretty much a deal breaker for me, although I don't feel like doing a clean install of 11.10, not tonight at least.

---

### Post by wyliecoyoteuk on 2012-05-18
What video card are you using?
and which driver?

---

### Post by fallofshadows on 2012-05-18
Unfortunately, I don't have a video card. My "video card" is built in to the laptop, it just pulls memory from the RAM to run video related stuff. Yes, it's horrible. 

As far as drivers, I don't know. I never had to install anything, I just plugged in the monitor and it worked. I haven't had any problems with it at all up until 12.04.

---

### Post by Grenage on 2012-05-18
You have one, it's just integrated; post the output of:

```
lspci | grep VGA
```

---

### Post by fallofshadows on 2012-05-18
And the result is:


00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

