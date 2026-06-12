---
title: "Monitor says &quot;No Signal&quot; when trying to load Ubuntu 10.10 from CD"
date: 2011-03-18
forum: General Help
---

### Post by rayofash on 2011-03-18
I was trying to boot Ubuntu 10.10 from a CD and it was going okay at first (gave me a 'loading' screen) and then everything went black and my monitor said it couldn't get a signal. I tried Fedora 14 and got the same problem. What's going on? I figure it's trying to set itself to a resolution my monitor doesn't support. My GFX card is an NVIDIA FX 5200.

---

### Post by mcclunyboy on 2011-03-18
how u connecting monitors?

---

### Post by TimEnid on 2011-03-18
are your monitors connected hdmi or dvi? or other?

---

### Post by rayofash on 2011-03-18
I don't know what those are. My monitor is a standard CRT. I don't know the name of the port, but it's color coded blue. It looks like this: [http://www.glofell.com/PIC/PIC/2010961957430.jpg](http://www.glofell.com/PIC/PIC/2010961957430.jpg)

---

### Post by securitymeddler on 2011-03-18
Hey! 

I had the same sorts of troubles a few years back when I first tried to get into Linux. I found that my video card and monitor just didn't detect right no matter what I did. 

Ultimately I replaced my video card, going from ATI to NVidia, which worked great. (site note, since then I have bought only NVidia card at home and work). There are ways around this by editing your video config file I think it's called xorg or something like that. If you install in text only mode. But to be honest it was a nightmare. 

I bought a cheap $5 video card off ebay, and my problems were solved.

You could also try installing with a separate monitor, then lower your resolution to a rate your CRT can handle then go ahead and swap them back out. 

By the way, if you are on older hardware it might be worth your time to check this out
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by rayofash on 2011-03-18
Yea it's called xorg. I've been having graphics problems with Ubuntu since the beginning but at least before it would actually display an image. How can I get into a text installer?

---

### Post by usatonycuba on 2011-03-19
> **rayofash said:**
> I was trying to boot Ubuntu 10.10 from a CD and it was going okay at first (gave me a 'loading' screen) and then everything went black and my monitor said it couldn't get a signal. I tried Fedora 14 and got the same problem. What's going on? I figure it's trying to set itself to a resolution my monitor doesn't support. My GFX card is an NVIDIA FX 5200.

1)-- Check your connections (all your connectors)
2)-- Open your Case, Unplug Battery, let sit for 5 to 10 Minutes
3)-- Get battery back on place, Power on, get into BIOS
4)-- Load Default Values on BIOS, F10, Save, restart.
5)-- Place your Ubuntu Installation CD-DVD, chose TRY FIRST WITH OUT INSTALL.
6)-- After loads, make install (chose install updates wile instaling)

Otherwise, there is a hardware problem.. GL

---

