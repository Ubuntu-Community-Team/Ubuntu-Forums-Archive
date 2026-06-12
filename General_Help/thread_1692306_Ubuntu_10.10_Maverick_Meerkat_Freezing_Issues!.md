---
title: "Ubuntu 10.10 Maverick Meerkat Freezing Issues!"
date: 2011-02-21
forum: General Help
---

### Post by Tentontitan on 2011-02-21
[FONT="Arial"]Hi,

I'm having frequent freezing issues within Ubuntu 10.10 and it's beginning to become a regular thing. I've come to find out that it only happens when the visual effects settings are at normal or extra. Everything will be fine for whatever amount of time but after a while the entire system freezes. I get no response from ANYTHING at all, not even the keyboard/mouse. This is really annoying and I'm not quite sure what to do. I'm mostly new to the whole Linux scene. Any help is appreciated!

Machine Specs:

Compaq Presario SR5250NX
Intel Pentium Dual Core @ 1.60 GHz
1GB Ram
Intel Graphics Media Accelerator 950[/FONT]

---

### Post by mihaimm on 2011-02-21
I have a very similar machine (Dell though) and I have no problems with 10.10. Try to see anything suspicious in the logs after a freeze (check [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/) for details on the available logs). 

If that doesn't help you shouldn't rule out a hardware problem. Do a memory check (I had similar problems with a defective memory on a different machine, freezes when using effects - the memory was shared with graphics and only with effects the 'wrong' bits were accessed).

Also... check the voltage settings on your CPU. Not sure if your BIOS allows undervolting but I had similar (random, rare freezes) due to setting 1.1V instead of 1.25V.

---

### Post by Tentontitan on 2011-02-21
[FONT="Arial"]Thanks, I'll check into it.[/FONT]

---

