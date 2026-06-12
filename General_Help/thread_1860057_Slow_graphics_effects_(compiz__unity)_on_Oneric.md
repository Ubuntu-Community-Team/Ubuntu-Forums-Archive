---
title: "Slow graphics effects (compiz / unity) on Oneric"
date: 2011-10-14
forum: General Help
---

### Post by gdi2k on 2011-10-14
Loving Oneric so far, but I'm finding the desktop effects much slower than on Natty. When dragging windows, the window lags behind the cursor and the new task switcher is basically unusable for me due to slowness. 

This only happens when the laptop is docked and connected to two external 23 inch monitors (each at 1920x1080). When the laptop is not docked, things are snappy, so I'm clearly reaching the limits of my graphics hardware when I have the external monitors connected. 

Hardware: Core2 Duo 2.40 GHz (P8600) with integrated GMA X4500HD graphics, 4 GB RAM. 

I've played with the compiz settings, but couldn't find any way to improve things. I've tried Unity 2D too, but it doesn't have feature parity with the full thing (can't reduce icon size for example). 

Does anyone have suggestions as to how I could improve things? I would be happy to sacrifice quality for speed if possible.

---

### Post by collisionystm on 2011-10-14
Gnome-shell is faster. Try it.

---

### Post by thatguruguy on 2011-10-14
> **gdi2k said:**
> When the laptop is not docked, things are snappy, so I'm clearly reaching the limits of my graphics hardware when I have the external monitors connected. 


That is indeed the problem.  The intel integrated graphics just aren't robust enough when trying to render in 3d on two monitors.

Unity 2d might be your best bet when running the 2-monitor set up.

---

### Post by gdi2k on 2011-10-15
Thanks for the suggestions. I did try Gnome 3 and you're right, it's fast. Much faster than even Natty's Unity in fact. But I can't use it - switching between applications is way too much hassle to be usable for me for day to day use. 

Unity 2D is fast too, but I can't change the launcher icon size and I don't want to live with the 48px kindergarten icons. 

Given the slowness of Unity, that Libreoffice is still missing its close / minimize / maximize buttons for Calc 8 times out of 10, the launcher frequently doesn't appear when I touch the left screen side (annoying!) and the Skype panel icon doesn't appear when external monitors are connected, I may switch back to Natty. What a pain.

---

