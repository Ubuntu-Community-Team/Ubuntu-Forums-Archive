---
title: "Reduce screen brightness below lowest default GUI setting."
date: 2011-01-06
forum: General Help
---

### Post by Consecrated on 2011-01-06
Hello all,

My notebook has a very bright screen even when on the lowest brightness setting using Ubuntu 10.10 64bit (and Windows). Is there a way to reduce the brightness further than the lowest default GUI setting to save batteries, perhaps via terminal or another program? Is this even possible? 

I have heard some others say that they wished the lowest setting took the screen down to black. I'm not sure this would be the best idea, but I would like to reduce the brightness to the same dim that Ubuntu mimics before the screen saver or when it requests my user password.

(I almost wouldn't mind having some sort of program to add grey pixels into the mix for the sole purpose of reducing eye strain at night.) 

Thanks!

---

### Post by Consecrated on 2011-01-13
Bump

---

### Post by JC Cheloven on 2011-01-13
I also find bothering too bright screens. Not sure if any of the following will fit you, but you can try:

- I like to work in a very dark room, specially in summer when I open the windows because of the hot. For that situation, the Super-N action of compiz puts in negative the window, which is what I need as most of the apps come with a very bright theme.

- I also put the slider in the energy manager at a low level. Not sure if that's what you told you did.

- If you have a proprietary controller for your GPU, you can try within its configuration tools (also, if it's an Nvidia you may try smartdimmer from the repos; If it's ATI, you may try raedontool).

- There are some other apps in the repos: xvattr, ddccontrol, gddccontrol, ... go for a walk through synaptic ;)

---

### Post by jromma on 2011-08-09
If you have an nvidia GPU and are using their proprietary driver, then just open up the control panel and go to "X Server Color Correction" and adjust the brightness for the desired screen. Works like a charm.

---

### Post by Gargoulf on 2012-07-31
xgamma -gamma 0.8

---

### Post by wildmanne39 on 2012-07-31
Hi, this is an old thread so it has been closed, thanks for sharing.

---

