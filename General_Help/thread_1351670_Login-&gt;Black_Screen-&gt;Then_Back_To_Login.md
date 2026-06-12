---
title: "Login-&gt;Black Screen-&gt;Then Back To Login"
date: 2009-12-10
forum: General Help
---

### Post by pspkr3w on 2009-12-10
so i login i see a black screen with words but its too quick to read then it goes back to login

---

### Post by pspkr3w on 2009-12-10
bump please need help i have 9.10 and  just updated restarted and can't login

---

### Post by dakine42 on 2009-12-10
This usually means you have something wrong with your Xwindows setup. Press CTL-ALT-F2 to get a text-mode login screen, and take a look at /var/log/Xorg.0.log for clues. If you don't see anything, try running "X -configure", then "startx" - if that works, copy xorg.conf ftom your home directory to /etc/X11 (sudo cp ~/xorg.conf /etc/X11), and reboot. That should fix X for you.

---

