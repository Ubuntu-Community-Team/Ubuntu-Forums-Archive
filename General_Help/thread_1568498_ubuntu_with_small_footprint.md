---
title: "ubuntu with small footprint"
date: 2010-09-05
forum: General Help
---

### Post by dek8 on 2010-09-05
I cant find the thread but some guy said he got ubuntu booting up on 40mb... is that even possible? how?

i got a minimalist ubuntu setup with xorg, xfce, alsa, nvidia drivers and synaptic and it boots on 140mb... how did he manage? 

are there any things to be done other than unchecking startup services to have it boot on less?

---

### Post by DemonBob on 2010-09-05
He might be using an window manager with a even smaller footprint in memory. i.e. lxde, or awesomewm.

---

### Post by dek8 on 2010-09-05
> **DemonBob said:**
> He might be using an window manager with a even smaller footprint in memory. i.e. lxde, or awesomewm.

oh crap, my xfce and plugins comes in about 90mb, i had no idea..

bit still fluxbox uses 40mb... and he got ubuntu on 40...

---

### Post by perspectoff on 2010-09-05
The Ubuntu server can be installed with a minimal installation option, which is pretty darn small.

LXDE (used for Lubuntu) is a pretty lightweight desktop, which can be added if you really want a desktop. 

I don't know what the final combined footprint is, however.

The new version of Puppy Linux, which is probably the best small footprint OS, now uses the minimal Ubuntu server as its basis. 

Check out Puppy Linux, as well.

---

### Post by Nythain on 2010-09-05
It's not to common but it's not unheard of. In order to get ubuntu to run on anything that small though is gonna require some kernel stripping and removing some of the bloat from the distro, way to much effort unless you are a real linux geek and just want to see how far you can push the envelope

and now for linkage to the most impressive install i've seen to date. it wasn't done with ubuntu, but i imagine you could skim ubuntu down pretty low too

[http://kmandla.wordpress.com/2010/08/13/x-and-openbox-in-12mb/](http://kmandla.wordpress.com/2010/08/13/x-and-openbox-in-12mb/)

---

### Post by QLee on 2010-09-05
[QUOTE=dek8]I cant find the thread but some guy said he got ubuntu booting up on 40mb... is that even possible? how?[/QUOTE]
My guess, he's probably not running an Xwindow. Likely doesn't need a GUI on that system.

---

