---
title: "A few fatal flaws when running LIVE CD."
date: 2006-04-12
forum: General Help
---

### Post by chris062689 on 2006-04-12
I loved the screenshots, I htink ubuntu is a great choice for me but.. I have two huge problems.

1) When I tried to run the CD, it booted the desktop environment, but gave me an error on my moniter (a blue box; totally black background)

"Out of Frequency Range
        (Displays red , green, and blue)
 Change screen res. and try again."

But there's no way I can =(

2) My fan runs constantly, I believe both fans (one to my hard-drive, and the main cooling fan) both run.  It gets really loud and annoying, (such as a sound when first starting up your computer; it stops whenever I boot into XP though)


Could anyone help me with both of the problems I have stated?

---

### Post by justleen on 2006-04-12
[QUOTE=chris062689]I loved the screenshots, I htink ubuntu is a great choice for me but.. I have two huge problems.

1) When I tried to run the CD, it booted the desktop environment, but gave me an error on my moniter (a blue box; totally black background)

"Out of Frequency Range
        (Displays red , green, and blue)
 Change screen res. and try again."

But there's no way I can =(

2) My fan runs constantly, I believe both fans (one to my hard-drive, and the main cooling fan) both run.  It gets really loud and annoying, (such as a sound when first starting up your computer; it stops whenever I boot into XP though)


Could anyone help me with both of the problems I have stated?[/QUOTE]


1)  open a terminal and run dpkg-reconfigure xserver-xorg
this will alow you to setup X for your monitor. Once done with this,(log out and) hit CTRL-ALT-BACKSPACE to restart X

2) Sure its not the CD drive?  since your booting from a live CD this will be running almost al the time. Since in XP it stops, i recon its just that XP checks the drive, and stops it when done..

---

### Post by chris062689 on 2006-04-19
I have my computer open right now, and the CPU fan is running, constantly.
It's installed to my hard-drive too.
I'm not running on a laptop.

---

