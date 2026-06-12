---
title: "Xubuntu Hangs Laptop"
date: 2010-05-13
forum: General Help
---

### Post by andrewklau on 2010-05-13
Hello,

I'm running Xubuntu on my laptop with an external monitor (larger than lcd internal monitor).

After running either come CPU intensive applications or simply after a while of being on both monitors completely freeze up with either a blank white screen or stripes. Laptop is frozen, does not respond to pings, and any keyboard input is not detected. I have no gfx drivers installed, but am using xrandr to custom set the external monitor settings. It is AMD and ATI laptop.

I have in boot options: noapic nolapic
Running Xubuntu 10.4 2.6.32-22-generic

I did find this to be one of the suspicious things in my logs:
May 13 23:00:00 andrew-laptop kernel: [    0.189852] Marking TSC unstable due to TSC halts in idle

Hoping for some help, thanks.

---

