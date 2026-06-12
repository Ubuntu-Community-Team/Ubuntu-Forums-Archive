---
title: "Video Driver Help"
date: 2009-08-30
forum: General Help
---

### Post by baker126 on 2009-08-30
Alright...I screwed up.  I was trying to install Guild Wars yesterday and ran into problems.  Thinking it was my driver for my video card, I went into Synaptic and switched it.  Everything seemed to work fine but all my windows had a black outline that was really annoying.  When I tried to change back, I couldn't figure out which packages to use.  Here is my setup:

HP Pavilion DV4 1140go
Intel Graphics Media Accelerator 4500MHD

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 2293
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 8110 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0
        Memory at d6500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

I have video now, but no 3D.  There are about 3/4 of the screen savers that are not allowing my to preview.

Thanks.

---

### Post by Liolikas on 2009-08-30
There is no many options for intel users just intel or vesa. For 3D you need intel. Intel screwed up a little 2.7[6].x series but 2.8.1 works just fine for me.

---

### Post by baker126 on 2009-08-30
Everything worked fine prior to my meddling hands.  Is there anyway to figure out which packages I need to take off and which need to be put back on to store my previous state?

---

### Post by Liolikas on 2009-08-30
Try simply sudo apt-get install **xf86-video-intel**

---

