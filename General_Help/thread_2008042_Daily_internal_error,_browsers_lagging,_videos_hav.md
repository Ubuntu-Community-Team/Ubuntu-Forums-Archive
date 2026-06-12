---
title: "Daily internal error, browsers lagging, videos have frozen twice today.."
date: 2012-06-21
forum: General Help
---

### Post by MoonLitOwl on 2012-06-21
So the first month of Ubuntu 12.04 was great. Hated Chrome, and wanted something lightweight so I put up Midori. Love it, aside from the fact that it's terrible at playing youtube videos, so I downloaded Opera just for that.

But lately, and on a daily basis, I get a message poping up as soon as either browser starts to lag (or I'm playing a video) that says "12.04 Internal error" with the option to send that information back in an attempt to fix it.

I'm getting really tired of this. Now even Midori is seriously lagging and it takes me forever to type anything up. And just today, I was watching a movie in VCL and the damn thing froze twice.

I had tried doing a fresh-install, but my comp just ended up doing with it did to me the first time I installed; frozen screen, stuck on the HP page, and when it finally did get to Ubuntu it was right back onto my regular login screen, not what's on my usb. 

I've even had Opera freeze completely and do nothing when I try to close it. The regular video player has done the same as well.

So I'm at a lose as what to do. I've no issues with downloading all the updates. I thought that maybe cleaning it up (like one would do with Windows) would help only.. Don't think that's even possible. And I haven't clogged it down with programs, I try to keep it clean and light.

Help!

Comp: HP Pavilion dm1
AMD E-350 Processor × 2 
Graphics: VESA: WRESTLER
64-bit

---

### Post by blackflame2996 on 2012-06-22
Does apport give the option for more details on the error? if so, please post the contents.

---

### Post by MoonLitOwl on 2012-06-23
> **blackflame2996 said:**
> Does apport give the option for more details on the error? if so, please post the contents.

No, just that there's an internal error in Ubuntu 120.4 lts and that if it shows up again to restart. =(

---

### Post by blackflame2996 on 2012-06-23
If you want, you can disable the error messages.

```
sudo nano /etc/default/apport
```

Change enabled from "1" to a "0" so it looks like this:

```
enabled=0
```

---

