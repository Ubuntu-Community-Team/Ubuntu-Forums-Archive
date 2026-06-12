---
title: "Is there a way to get better mouse sensitivity without mouse acceleration?"
date: 2009-12-02
forum: General Help
---

### Post by Cytochromec on 2009-12-02
Hello, I need high mouse sensitivity without any acceleration. I find the acceleration too inconsistent and its hard to get accurate with my mouse since its a bit unpredictable at times. I have the sliders at max sensitivity and no acceleration and that is way to slow. I have to opposite, but its not the same as a super stable windows (ya, I said stable windows!) mouse setup with high sensitivity. Is there anyway to achieve better mouse sensitivity without acceleration? I looked through synaptic and google and found nothing. Linux users cant all be keyboard warriors!

---

### Post by gatman3 on 2009-12-14
Not sure, of course, but no acceleration is probably not exactly what you want.  With no acceleration you would have to move your mouse a pretty long physical distance to get where you want to.

Perhaps you have other mouse sensitivity problems.  I recently ran into a problem where, for various reasons I won't go into, I was messing with my Xorg configuration and screwed up my mouse sensitivity completely.  Looking into the configuration pages in KDE (sorry if this doesn't help with GNOME) the only relevant setting was mouse acceleration.  Yet mouse acceleration was not really the issue I was having, not exactly sure how to describe it, but it was more like there was some inertia in moving the mouse before it would detect motion, and then the precision of the pointer on the screen relative to how I moved the mouse was very poor.

In any case, it seems that the solution for me was adding the following into the /etc/X11/xorg.conf file:

```
Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "ConstantDeceleration" "3"
EndSection

```

After doing that, I am seeing very precise mouse behavior.  I cranked the mouse acceleration down to 1.8x in the system settings, and that seems about perfect for me.  If I crank it down to 1.0x, as you suggest you would like, I have perfect precision now but I have to move my hand very far to get from one side of the screen to another.

Anyhow, don't know if this will solve your problem, but since no one else was helping you I thought I'd make the suggestion.

---

