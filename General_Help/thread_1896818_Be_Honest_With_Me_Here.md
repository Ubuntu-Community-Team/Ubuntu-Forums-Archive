---
title: "Be Honest With Me Here"
date: 2011-12-17
forum: General Help
---

### Post by ThePhysician on 2011-12-17
What Linux distro do you think has the best triple monitor support?

I tried the first Ubuntu that had Unity and it was a piece of filth when it came to my XFX ATI HD 5870, the monitors flickered and the windows broke when dragged no matter what I did. 

I currently play EVE Online on 3 monitors with Eyefinity support on  Windows. Is this impossible with all distros of Linux?

I don't wanna keep using windows but I feel forced. =(

---

### Post by ThePhysician on 2011-12-17
Gnome 3? Gnome 2? Unity? Other distros/types?

---

### Post by 4Orbs on 2011-12-17
Even though I'm an Xubuntu user, the quickest way to have dual monitors (don't know about three monitors) working was to install the KDE desktop and then the proprietary drivers for my HD 5770, then log into the KDE session and use the (ati) Catalyst Control Center to configure the monitors. I think Kubuntu is just fabulous also.

Your problem with window tearing may be more related to the Unity sync-to-vblank settings in Compiz than the distro or desktop environment.

---

### Post by Dlambert on 2011-12-17
Do you have/had the latest ATI/AMD Drivers? And he is asking about tri monitors.

---

### Post by ThePhysician on 2011-12-17
I did at the time, but it was 10.10, and I think Compiz/Unity has problems with 3 monitors. So should I just go with Kubuntu or Xubuntu? Do both have or lack Ubuntu Software Center? 

Also.. Gnome 3? Would that work? Or is that still a mess like it was back around the 10.10 time?

---

### Post by 3Miro on 2011-12-17
> **ThePhysician said:**
> Gnome 3? Gnome 2? Unity? Other distros/types?

Those are not distributions. Gnome 2 is a desktop environment. Unity an interface on top of Gnome 3. The default Gnome 3 interface is Gnome-shell.

The newer environments may be lacking in terms of exotic support. You can try some of the environments that have been around a bit longer, like KDE or XFCE.

To be honest, if I have to guess, I would say that the issues that you are experiencing are related to the ATI driver. Try to get a distribution with the latest ATI driver (or install an unofficial ppa if you have to).

---

### Post by 3Miro on 2011-12-17
> **ThePhysician said:**
> 
Also.. Gnome 3? Would that work? Or is that still a mess like it was back around the 10.10 time?

10.10 comes with Gnome 2, you can only get Gnome 3 via unofficial ppa and hence things were buggy. 11.04 and 11.10 come with Gnome 3 by default.

I would try 11.10 for the latest ATI driver.

---

### Post by Buntumatic on 2011-12-17
Not being an Ubuntu user myself I cannot tell what to install to achieve triple monitor support with *buntu.
However, rebuilding (as in compiling) your X server and apps with xinerama support will give you support for three or more displays, no problem.

---

