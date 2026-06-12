---
title: "Quad monitor setup"
date: 2012-05-01
forum: General Help
---

### Post by oshirowanen on 2012-05-01
I have a new computer with 2 identical graphics cards and 4 monitors as each graphics card has a dvi and vga port.

Only 2 of the monitors seem to work out of the box.

How do I get all 4 working?
 
I have 2 nVidia GT520 cards (not the most powerful of graphics cards, but it's not a gaming machine)  and I have 4 19" monitors, all with a native resolution of 1280x1024.  I have installed the nvidia proprietary drivers and Unity3D is working.

I don't mind giving up Unity3D compositing/effects to get all 4 monitors working if it comes to that.

So to sum up, when I connect all 4 monitors, I can see all of them in the nvidia settings app, but only 2 of the screens actually display anything.  If I go to the Ubuntu displays dialog box, I just see 1 big screen.

In the nVidia settings dialog I'm getting:

    GPU 0 - (GeForce GT 520)
    CTR-0-(CTR-0)
    CTR-1-(Acer AL1916)
    GPU 1 - (GeForce GT 520)
    CTR-0-(CTR-0)
    CTR-1-(Acer AL1916)

I would have thought I should be getting something like this instead?

    GPU 0 - (GeForce GT 520)
    CTR-0-(Acer AL1916)
    CTR-1-(Acer AL1916)
    GPU 1 - (GeForce GT 520)
    CTR-0-(Acer AL1916)
    CTR-1-(Acer AL1916)

Can someone please advise me on how to get this working?

---

### Post by oshirowanen on 2012-05-02
I think the reason why 2 of the monitors are being identified by their id is not being sent to nvidia settings properly is because I have cheap dvi2vga adapters?

Which dvi2vga adapters would I need to get which are capable of sending the monitor id to the graphics card?

---

### Post by oshirowanen on 2012-05-03
Any help will be appreciated greatly.

---

### Post by oshirowanen on 2012-05-05
Got it working.  Thanks.

---

### Post by bullium on 2012-06-02
> **oshirowanen said:**
> Got it working.  Thanks.

Did you get it working with Unity3D or Unity2D? I've got an HP Z600 Workstation with an NVIDIA NVS450 and can only get the 4 displays working properly with Unity2D. I'd love to get Unity3D working if I could.

---

### Post by oshirowanen on 2012-06-07
> **bullium said:**
> Did you get it working with Unity3D or Unity2D? I've got an HP Z600 Workstation with an NVIDIA NVS450 and can only get the 4 displays working properly with Unity2D. I'd love to get Unity3D working if I could.

I can only get it to work with Unity2D and Gnome Classic.  It can't get this to work with Unity3D.

---

