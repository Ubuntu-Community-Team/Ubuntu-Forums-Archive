---
title: "Major graphics problem"
date: 2010-12-07
forum: General Help
---

### Post by kitsune7 on 2010-12-07
Okay, I have Ubuntu 10.10 installed on my system.  Sometimes (often after a drag effect) everything on screen freezes and becomes completely unresponsive to anything but my mouse.  I am required to do a hard reset each time this happens.

Other times (don't even know what could trigger this) my computer doesn't freeze but it messes up the graphics majorly.  When I mouseover the panels on my desktop (set to autohide) lines show up where my panel should be but it isn't all displayed.  The buttons will show properly after moving the mouse over them and any image (such as the network icon) that changes state becomes clear, but the next time I mouseover the panel it gets messed up again.  At the same time this happens I can't move a window around or scroll within any window without the display going crazy.

Any help?

---

### Post by NoBugs! on 2010-12-11
What graphics card/driver is it using? Does it have the same problem when you turn off compiz effects (prefs-appearance-effects)?

---

### Post by kitsune7 on 2010-12-12
Using lspci I was able to get this for my graphics card information:

01:00.0 VGA compatible controller: **Silicon Integrated Systems** [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA controller])
        Subsystem: **Hewlett-Packard** Company Device 2a06
        Flags: 66MHz, medium devsel, IRQ 12
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 9000 [size=128]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel modules: sisfb

(I bolded some information)
I can't enable any compiz effects at all.  It checks for new drivers and then stops and says it can't enable effects.  I'm stuck on the "No effects" setting.

Strange that it says Hewlett-Packard.  I have a Compaq Presario computer...

---

### Post by kitsune7 on 2010-12-15
I'm thinking it might help if I try to use the vesa driver but my xorg file is missing.  Even when I reconfigure xserver it doesn't help.

---

### Post by kitsune7 on 2011-01-10
Okay my problem is now solved.  I just got a new graphics card and it works great. :D

---

