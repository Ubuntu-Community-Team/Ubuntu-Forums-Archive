---
title: "Virtual Desktops and HDMI Out"
date: 2011-05-16
forum: General Help
---

### Post by Rikeshar on 2011-05-16
Hey there everyone, I had a question:

I have a video card with an HDMI out port. I was wondering if it would be possible to assign a virtual desktop to this HDMI out, so that I could run XBMC on one desktop and to the TV, while doing other stuff on a different virtual desktop on the computer monitor.

Any way to do this?

---

### Post by gsmanners on 2011-05-16
It depends on your hardware. You probably can, although configuration can be a real pain (especially if we're talking about an ATI card).

---

### Post by Rikeshar on 2011-05-16
It's EVGA GeForce GT430. Any ideas on how I might set it up? Or where I might look?

---

### Post by gsmanners on 2011-05-16
If the nvidia driver works with that card, you can then run:

```
gksudo nvidia-settings
```

Then you can just configure your monitors whatever way you want.

---

### Post by Rikeshar on 2011-05-17
Hm... I don't see from that how I'd set up the HDMI to pull from a specific virtual desktop. I don't have the HDMI cable just yet though, maybe once it's plugged in some other option will become active in those settings. Thanks for the response though, at least I know now that it's at least possible!

---

