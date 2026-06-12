---
title: "Moving Mouse Kills CPU??"
date: 2009-09-12
forum: General Help
---

### Post by JordanMaster22 on 2009-09-12
Why does moving my mouse simultaneously take up almost 90% in Ubuntu 9.04?  In Windows it only uses 7%.  Is there any way to fix this?  Like maybe a driver that uses the mouse differently?

Pentium 4 2.0 GHz Processor

Microsoft Comfort Optical Mouse 2000 1043 USB

---

### Post by 3rdalbum on 2009-09-12
Wow... moving your mouse in Windows takes up 7% of your CPU capability? That's 7% too high.

I'm sorry but I've never heard of this problem. If you have an Nvidia or ATI graphics card, have you got the proprietary drivers installed?

---

### Post by harrismh777 on 2009-09-12
> **JordanMaster22 said:**
> Why does moving my mouse simultaneously take up almost 90% in Ubuntu 9.04?  In Windows it only uses 7%.  Is there any way to fix this?  Like maybe a driver that uses the mouse differently?

Pentium 4 2.0 GHz Processor

Microsoft Comfort Optical Mouse 2000 1043 USB

Start two programs:

    System-->Administration-->System Monitor

    Applications-->Accessories-->Terminal

In the termincal window enter the command, "top"   without the quotes.

Now, move your mouse all over the screen and watch the display. In top you should see xorg rise to "the top" with a given amount of cpu%, etc. The system monitor will show you a graph of the amounts of memory, cpu utilization, etc.

Is something other than xorg at the top?

How much memory do you have available?  How much swap?   Are system resources adequate for linux... memory, swap, etc?

My guess is that the mouse is not taking the cpu, rather, something else coincidentally is taking the cpu.  I had a similar problem with my laptop on wifi connect... the network manager takes over the desktop *not nice* during connect so that the effect is that the mouse responds slowly and appears to be killing the cpu... when in fact the culprit is network manager. 

With nothing else going on, and while moving your mouse around the screen rapidly (assuming no fly over texts) xorg should not take more than about 7 %.  I can drive mine just a little higher if I try.

---

