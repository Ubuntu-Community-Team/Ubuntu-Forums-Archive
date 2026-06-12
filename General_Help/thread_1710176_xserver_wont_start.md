---
title: "xserver wont start"
date: 2011-03-19
forum: General Help
---

### Post by unbuntunewb on 2011-03-19
So I tried to install nvidia drivers, now for some reason when Im at the command line, ctrl alt f1, and I try to get back to the desktop by the typing in "startx" nothing happens, why is this?

---

### Post by andrewthomas on 2011-03-19
What card/GPU do you have?

How did you go about installing the driver?

Do you have nvidia-current installed?

Is your GPU supported?

> GPUs such as GeForce series 6 or newer are supported. 
 See **/usr/share/doc/nvidia-current/README.txt.gz** for a complete list of supported GPUs and PCIIDs       


---

### Post by unbuntunewb on 2011-03-19
I have a geforce 9500 gt. I tried installing the drivers from the website but that absolutely would not work so I just used the nvidia x server drivers from synaptic.

also I should be more clear. I have a desktop that works fine. When I am on my desktop and I press ctrl alt f1 to get to the command line and I want to return to my desktop when I type startx I get errors.

---

### Post by andrewthomas on 2011-03-19
If you already have an xserver running, then press <CTL>+<ALT>+<F1> to get to a terminal, 

to return to the xsession you do not then startx, 

you would **<CTL>+<ALT>+<F7>** or **<CTL>+<ALT>+<F8> **to return to that session.

---

### Post by unbuntunewb on 2011-03-19
Ill give it a try thank you

---

### Post by unbuntunewb on 2011-03-19
It worked! thanks a bunch

---

### Post by andrewthomas on 2011-03-19
You're welcome. 
 
Could you please mark the thread as [SOLVED] using the thread tools menu?

---

