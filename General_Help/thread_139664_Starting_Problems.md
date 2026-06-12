---
title: "Starting Problems"
date: 2006-03-04
forum: General Help
---

### Post by Natalie Erin on 2006-03-04
Hello, 

I was wondering if anyone would be willing to assist me with my problem.  I recently installed Ubuntu 5.10 and had to do a major work around to get it to work.  I finally got it installed, but it freezes every time after it loads the display manager.  I can get it to load up in recovery mode, but can't quite figure out why it continues to freeze during a normal startup.  I would love any advice or help that anyone can provide,

Thank you.

---

### Post by arctic on 2006-03-04
Sounds like a graphic card problem. What hardware do you have?

---

### Post by suRoot on 2006-03-04
What exactly was this "work around" you had to pull to get it installed?  Can you tell us anything about your computer - what brand, what video card, etc?

When it freezes, can you switch to a console?  After booting, try pressing ctrl+alt+f1 & see if you get a login prompt.  If so, login & have a look at /var/log/Xorg.* to see if you see any errors in the log.

If you're unable to switch to a console, you've got a more nefarious problem & we'll need to go about fixing it another way.

---

### Post by Natalie Erin on 2006-03-04
[QUOTE=suRoot]What exactly was this "work around" you had to pull to get it installed?  Can you tell us anything about your computer - what brand, what video card, etc?

When it freezes, can you switch to a console?  After booting, try pressing ctrl+alt+f1 & see if you get a login prompt.  If so, login & have a look at /var/log/Xorg.* to see if you see any errors in the log.

If you're unable to switch to a console, you've got a more nefarious problem & we'll need to go about fixing it another way.[/QUOTE]

Processor:  AMD - 3400
RAM: 1 GB
Motherboard: NVidian NForce 3
Video Card:  ATI 9800 Radeon Pro

If there is anything else in terms of computer necessities let me know.  

And no, I can not switch to a login prompt.  It is completely frozen.  I have to manually reset my computer.

Thanks.

---

