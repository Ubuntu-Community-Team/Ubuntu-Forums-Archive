---
title: "Old computer cannot run graphics. How do I disable them?"
date: 2009-08-08
forum: General Help
---

### Post by gksudo on 2009-08-08
Hello,
I have a dell dimension 2300 that's from 2003. and obviously it can't run any of ubuntu's default graphics. So after I login, it doesn't display anything but a black screen and a mouse cursor.Does anyone know how to disable the graphics without going into the gdm. Something like a failsafe terminal or recovery mode. 
Any help would be much appreciated.:D

---

### Post by mikewhatever on 2009-08-08
A relative of mine used to run Ubuntu on a PC from 1998, and I assume there should be no problem with your computer, provided its graphics card has Linux support. Why don't you post your computer specs, CPU, RAM, graphics.

---

### Post by doas777 on 2009-08-08
if you just need to turn off compiz, just hit Alt+ F2, and type:
```
metacity --replace
``` and hit Enter.

I usually can't see a screen while I'm doning this, but it usually works, when I'm VNCing into a box with compiz enabled.

---

### Post by Bladehawke on 2009-08-08
I'm running ubuntu on a P3/933 with 512MB RAM and intel i810 video.  Nothing manufactured in 2003 is worse than that

---

### Post by lswb on 2009-08-08
There's no reason a gui won't run on a 6 year old system or even a 10 year old system. Or are you talking about compiz/special effects graphics? Either way, when booting, select recovery mode from the grub menu; If ubuntu is the only installed OS on the computer you may have to press the escape key during boot to make the grub menu visible.

One of the recovery mode options is for trying to fix graphics mode, I forget the extact title right now, but select that and see if it helps.

---

### Post by dcstar on 2009-08-08
> **gksudo said:**
> Hello,
I have a dell dimension 2300 that's from 2003. and obviously it can't run any of ubuntu's default graphics. So after I login, it doesn't display anything but a black screen and a mouse cursor.Does anyone know how to disable the graphics without going into the gdm. Something like a failsafe terminal or recovery mode. 
Any help would be much appreciated.:D

Install the Server edition of Ubuntu or the Alternate, otherwise do a forum search for disabling the GDM and you should find detailed instructions.

---

### Post by soapBAR2 on 2009-08-08
> 
**DELL DIMENSION 2300:**
Pentium 4
1800 MHz
256 MB (max 1024 MB) SDRAM
Intel 845GL Chipset
Integrated Intel 845GL Graphics w/ 16MB RAM
40 GB ATA
48XCDROM, Floppy
10/100mbps Ethernet Card
200W PSU


Your computer should be more than fast enough to run Gnome - I've run Ubuntu on a 1.5GHZ P4, 128MB ram and integrated video (16mb). If your problem hasn't been solved by the above posters (ie, turn off compiz), I'd suggest switching to Xubuntu, since it's a lot more lightweight.

---

