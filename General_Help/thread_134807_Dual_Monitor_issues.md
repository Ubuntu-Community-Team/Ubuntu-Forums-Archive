---
title: "Dual Monitor issues"
date: 2006-02-22
forum: General Help
---

### Post by krmiller on 2006-02-22
I have a Dell Latitude 610 (ATI video) with a port replicator.  On the back of the port replicator is a VGA and DVI output.  I also have dual identical LCD monitors.  On monitor connects to the VGA and the other to the DVI.  

I am able to run "big desktop" "clone" and "dual desktop" without major issues.  I run dual desktop which creates one session on each monitor.  The problems is that on the LCD monitor where the VGA connector goes, the bottom portion of the screen gets cut-off.  The LCD screen does not allow me to resize, just move, so no matter what I do I am missing part of the screen.  The monitor that is connected to the DVI output looks great and nothing is cutoff.  

The native resolution of the LCD monitors are 1280x1024, I have also tried to reduce to 1024x768 and still have the same issues.  

I am using the fglrx drivers.  Initilally the 8.10 and recently upgraded to the 8.22.05 drivers.  

Any help would be appreciated

---

### Post by krmiller on 2006-02-23
ttt

---

### Post by noahlt on 2006-02-23
Have you tried Xinerama?

---

### Post by Prospero2006 on 2006-02-23
Once you achieve Oneness with your xorg.conf file, 
you will easily attain Twoness.

Pros
Zen Master

---

### Post by krmiller on 2006-02-23
Yes, I have tried xinerama but I have the same issue there.  

For the second response....Everything works great with 1 monitor or without a monitor (just the laptop screen).  

I am thinking that this is an issue with the VGA port vs DVI.  The problem always follows the VGA port.   This may be an ATI driver issue but I have tried several versions of drivers.

---

### Post by mcewanbr on 2006-08-03
I am having the same issue.  All of the recent lattitudes use the same port replicator.  It appears that it some how splits the video directly off of the laptop's video card and does not contain a card in itself.

When I do a dmesg shows that the main card is on bus PCI:1:0:0.  When I boot into windows, it shows that the second (vga) video out is PCI:1:0:1.

I have been banging my head against this for some time now.  I have tried to configure my xorg.conf file to use the PCI:1:0:1 as the second display with no luck.

Any xorg guys here that can lend an idea?

---

### Post by mcewanbr on 2006-08-08
I was able to devote some bandwidth to this issue yesterday.  If I use the "nv" driver, it will send video through my DVI port.  If I use the "nvidia" driver, it sends it through the VGA port.

Any ideas?

---

### Post by maraflux on 2006-08-29
I'm having the same issue with NVIDIA Corporation NV43GL [Quadro FX 540] card. Anyone had any resolution yet?!
thanks

---

