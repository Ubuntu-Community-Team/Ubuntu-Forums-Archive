---
title: "Screen resolution only 800x600"
date: 2009-08-02
forum: General Help
---

### Post by Unreal223linux on 2009-08-02
I'm in the process of resurecting an old desktop for a family member. When I say old its OLD. Its an HP Pavillion 520w(256mb ram, 1.2ghz). It ran xp but the HD died, so I replaced them and installed xubuntu. It runs pretty smooth. 

Only problem now is the screen resolution is stuck at 800x600. This computer should be good for at least 1024x768 or higher. Its on a 17in crt. 

I have xubuntu 9.04 on here. Can anyone tell me how to fix this?

---

### Post by Vaphell on 2009-08-02
are you sure you got proper video drivers installed? 800x600 suggests that generic vesa driver for gfx is loaded.

---

### Post by Unreal223linux on 2009-08-02
I assume its just using the opensource driver. This computer is using an old onboard intel graphics set.

---

### Post by Tipped OuT on 2009-08-02
> **Unreal223linux said:**
> I assume its just using the opensource driver. This computer is using an old onboard intel graphics set.

Your graphics card could have lost support in 9.04.

---

### Post by DarinB on 2009-08-02
life was hell for me with this. i ended up getting a cheap 15 inch flat screen and it worked, i also had no problem with earlier releases or with Debian, pc linux but i must qualify that my problem was with nvidia older cards. borrow a flat screen and see if it works. no matter what people think i believe it was my crt.

---

### Post by RHTopics on 2009-08-02
I run into a similar situation when using Ubuntu with an uncommon monitor (Microtek C89) that is not automatically recognized.

In my case I keep a copy of a "xorg.conf" file that I knows works with that computer/monitor combination and copy it to the /etc/X11 directory.

A Knoppix Live CD, say version 5.1.1, does a good job in recognizing hardware.  You might try using Knoppix, see if it works at a higher resolution, and if it does, make a copy of its /etc/X11/xorg.conf file and use it with xubuntu.

---

### Post by Unreal223linux on 2009-08-02
I found my fix, pitty it wasn't with ubuntu.
I opened openoffice and software updates at the same time on this computer... bad idea, it took a whole 5min for openoffice to come up.

I had heard of puppy linux for old hardware and tried it, guess what?
It runs a wizard at start up to set screen resolution. So not only does it perform better, it is saving me from spending hours trying to fix a dumb problem!

---

### Post by Aguamiga on 2009-08-26
Had the same sort of problem, and solved it by having Xubuntu 7 generate a correct Xorg.conf file! (You don't need to install version 7, just boot from the cd)

For more info, read this post: [[COLOR=#444444]http://ubuntuforums.org/showthread.p...03#post7850803[/COLOR]]("http://ubuntuforums.org/showthread.php?p=7850803#post7850803")

---

