---
title: "Make Compiz less laggy?"
date: 2010-04-16
forum: General Help
---

### Post by adamant715 on 2010-04-16
How do I make Compiz less laggy? I'm running the default settings with docky and docky runs very laggy, and its very laggy when I minimize windows.

How do I make it super smooth just like Metacitys Composite feature? I am currently using it, but Compiz is just too slow. I miss the features compiz has. :(

---

### Post by RedSingularity on 2010-04-16
What graphics card are you running?

---

### Post by adamant715 on 2010-04-16
I believe I am running Nvidia Geforce 7300

---

### Post by RedSingularity on 2010-04-16
Did you ever install the proper drivers for that hardware?

---

### Post by SmSpillaz on 2010-04-19
Turn on things like vsync, change the AA to 1x and disable unneeded plugins to prevent excessive cpu usage which leads to less cpu time being given to screen redraw operations.

I have a GFGT8600 and I find that these things help. Also - if you don't care too much about battery life then you can keep things like blur on - since they will cause powermizer to stop downclocking your card.

WRT things like docky, as far as I can tell it renders using some raster algorithm, which is quite well optimized, however this has historically been slow on the nvidia driver. If you really can't stand it then try using cairo-dock (/gl-dock) since they have an opengl rendering method which works much faster.

---

### Post by Click-dot-Bejo on 2010-04-19
Are u using ubuntu 9.10?

---

### Post by fabounet on 2010-04-20
Use GLX-Dock, it's much faster than any other dock.
You have an nVidia so I guess there won't be any graphic problem with it (use the latest stable version).

---

### Post by _0R10N on 2010-04-20
I think that the problem resides on the misbehaviour on the management of the windows, caused by overlapping effects. I have a goddam good graphic card and I still have some issues. I know I should try deactivating a couple of effects, but... let's face it, everybody loves full featured compiz!!!

Kind regards!!

_0R10N >>

---

### Post by jkxx on 2010-04-20
Using Kubuntu 10.04 here with a Nvidia GeForce 8800GTS with Nvidia's drivers - so I have OpenGL and compositing enabled through kwin. 

Anyway the following couple things have helped:

1) Don't use specialty window decoration engines. If you are in Gnome, use one of supplied themes instead. Those extra engines really slow things down. For me it means sticking with Oxygen (KDE) rather than using the nicer Aurorae theming engine.

2) *don't recommend this* You could renice Xorg and compiz to give them higher priority which makes for smoother desktop effects. However, I'd avoid setting either to high priority or scheduling them as realtime as it could cause serious problems if either of those crashes.

I just did 2) before typing this and I did get smooth window animations with packages installing in the background. Again though, this can impact system stability so I'd wait till you get some more advice before trying it.

EDIT: Doing 2) might not be necessary if you use a preempt kernel though again I'd read the forum topics first. Will probably post back once I've tried it.

---

### Post by realzippy on 2010-04-20
> **RedSingularity said:**
> Did you ever install the proper drivers for that hardware?

This question should be answered...

---

