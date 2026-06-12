---
title: "random recoverable red screen in Unity 11.04 64bit"
date: 2011-06-17
forum: General Help
---

### Post by Ross Gayler on 2011-06-17
I am a Linux noob, so any of the following may make no sense.

I am running Ubuntu 64bit on a laptop (HP EliteBook 8540w).  It was set up by someone else with Ubuntu 10.10 64bit and was running OK.  I used the automatic upgrade to install 11.04 64bit and now have three problems: random power-off, random recoverable red screen, encrypted disk password prompt every second boot.  I am posting these problems separately on the presumption they are not symptoms of the same underlying cause.

** random recoverable red screen **

I am using the default Unity display manager.  A few times a day I get a red screen.  This appears to only occur while I am actively using the system.  I haven't noticed it happen when the system has been sitting idle.  Moving the mouse, typing, (un)plugging cables and USB things doesn't make the red screen disappear.  Pressing the <super> key (Windows logo) makes the red screen disappear reliably and instantly. When the red screen disappears the display is exactly as it was before the red screen appeared and everything is working correctly.  (If I had to guess, I'd say it looks like all the applications have carried on fine but the software that renders the applications to the screen has hung/crashed.)

I have no idea where to start looking to investigate this, so all suggestions are welcome.

---

### Post by Ross Gayler on 2011-10-19
This turned out to be bug #812040

I upgraded to Ubuntu 11.10 and the problem went away.  I have no idea if this is because the problem was intentionally fixed or some other changes incidentally happened to prevent the circumstances under which the problem was exposed.

---

