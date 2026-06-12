---
title: "Its still happening, its still Screen Rez problems"
date: 2011-02-20
forum: General Help
---

### Post by jackhe22 on 2011-02-20
Hello Ubuntu Community,

I really cannot count the ammount of times now, I've started a post related to Screen Resolution problems and you guys just can't seem to fix it; hopefully this time you can.

I've got myself a bootable Ubuntu stick right here ready to test, but as always, when I boot, the Boot Screen comes up like normal, except that its in 640x480, then when my Live Desktop should appear, I get my monitor telling me that its Mode Not Supported: 2048x1546. This has happened now, to me 16+ times, and its getting REAL BORING. :( I love Ubuntu, but the hassles I go through to get it running on my Box are just...
The actual maximum of my monitor is 1280x1024 @ 75hz, not that stupid high one.

What might be some help, is that Windows 2000 (the OS on the machine) also thinks that the maximum res is 2048x1546, leading me to believe that its an EDID signal problem.

If anyone can either help me:
Fix my EDID
Get Ubuntu to Boot Properly
or Give me this complicated script I'll give up on

Please reply. 

(Monitor is: Phillips PHP-X17)
(Card is: GeForce 7600GS AGP 256MB, authough in Windows, it says its a PCI card?)

---

### Post by jackhe22 on 2011-02-20
Bump

---

### Post by mtbower07 on 2011-02-20
What video card are you using?

---

### Post by jackhe22 on 2011-02-22
I did say at the end of my first post anyway:
GeForce 7600 GS AGP, although I tried my monitor with an old GeForce FX 5200, and it did the same thing in 2000 and in Ubuntu.

---

### Post by Grenage on 2011-02-22
> **jackhe22 said:**
> I did say at the end of my first post anyway:
GeForce 7600 GS AGP, although I tried my monitor with an old GeForce FX 5200, and it did the same thing in 2000 and in Ubuntu.

This should be an easy fix.  First, change your monitor cable; if you don't have one, can't change it, or that doesn't help, I'll knock you up an xorg.conf file that will sort it for you.

---

