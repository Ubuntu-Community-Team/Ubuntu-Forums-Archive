---
title: "password prompt invisible when screensaver active"
date: 2010-01-04
forum: General Help
---

### Post by metamatt on 2010-01-04
Hello,
presently my laptop requires a password when the screensaver has been activated (equivalent to the lock screen function).  However, when I move the mouse to activate the password prompt, the screensaver freezes (all movement stops) and the password prompt is not visible.  It's definitely there - if I type my password, then it brings me back to my desktop.  So far this hasn't been problematic.  However, if I mistype the password, or accidentally hit the mouse button so that somewhere other than the invisible password field is brought to focus, then entering the password becomes impossible, and I have to do a hard restart (ugh).  

I'm running an HP Pavilion dv5 laptop, with Ubuntu 9.10.  

Any suggestions on getting the password prompt visible from the screensaver?

---

### Post by jamesisin on 2010-01-04
I don't have a solution for your issue, but I can offer some meager advice if you lose focus on the password dialog so you don't necessarily have to hard-boot.

You'll have to turn ssh on.  Then if this happens again you can ssh into the machine and kill the password dialog (it's called something like gnome-screensaver-password but I don't remember exactly).  I've had to do this before.  I don't like hard-booting my boxes.

---

