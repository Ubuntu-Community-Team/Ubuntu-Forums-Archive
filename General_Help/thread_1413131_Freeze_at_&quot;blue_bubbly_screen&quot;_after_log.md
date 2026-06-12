---
title: "Freeze at &quot;blue bubbly screen&quot; after login"
date: 2010-02-22
forum: General Help
---

### Post by williamo123 on 2010-02-22
Hi, I would appreciate any help because I cannot access my system.  While I was trying to install a package in the package manager I accidentally removed a package that I am not aware of.  I got a crash report telling me to enter something along the lines of a broken package repair mode.  The next time I started my computer it froze at the blue screen with bubbles after login.  Is there a way to access the gui using a recovery/rescue type mode so I can access the package manager, or is there a way to find and reinstall the vital package?

---

### Post by Jackzor on 2010-02-22
Um. I'm not sure if this will help or not but...,

I had problems getting past the log on screen on 10.04 so I booted to the recovery kernal and started a root shell. From there I logged in and typed "startx" with no quotes. You can try that and if it works then fix your problems and RESTART as fast as possible. You can really mess you comuter up that way.

---

### Post by rnerwein on 2010-02-22
hi 
you said you get this blue screen after ! login. try, if the former post don't work, to get a terminal session - after login and that blue screen using "Ctrl + Alt + F1 (or F2 ..) and have a look at your .xsession-errors in your ~/ folder. mostely you can get there usefull information if there is a problem with graphical applications.
ciao

---

### Post by williamo123 on 2010-02-22
Thanks for the help so far.  I tried xstart at the recovery prompt and all I got was a black screen with a cursor.  As for .xsession it was not of any use because I cannot access the internet to download the packages that were deleted.  Is anyone aware of rescue/recovery methods for karmic that I could use to access my gui, or at least the package manager and internet?

---

