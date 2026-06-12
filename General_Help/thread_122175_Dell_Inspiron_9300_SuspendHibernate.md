---
title: "Dell Inspiron 9300 Suspend/Hibernate"
date: 2006-01-26
forum: General Help
---

### Post by jpfinley on 2006-01-26
I have seen this question posted in the forums here many times, but I will try once more in the hopes that someone has found a solution.

Does anyone actually have suspend and/or hibernate functions working on their Dell i9300?  I have checked out  [http://www.rtr.ca/dell_i9300/](http://www.rtr.ca/dell_i9300/) but still no luck.  I tried to see what was going on in System > Preferences > Power Preferences.  I receive this error when I open those preferences: ```
You have not got DPMS support enabled in gnome-screensaver.  You cannot change the screen shutdown time using this program.
```  After clicking OK on the dialog, the preferences itself has a blank Options tab.

Does anyone know if this error means anything, is fixable, or is related to suspend/hibernate functions?

This is one of the few things preventing me from going all-out Ubuntu.  I hope to get this working.  My machine is a Dell i9300 with Nvidia GeForce Go 6800, gig of ram, 80GB, WUXGA, running Breezy.

---

### Post by dresdn on 2006-01-27
I hate to say this, but I think you're out of luck due to your Nvidia card.  We have 2 9300's with the Nvidia card, and suspend/resume works just fine - it just doesn't post the video card upon restart.

I've seen people do it with the ATI cards on the 9300 without a problem, but until Nvidia fixes their Linux drivers, we're out of luck.

---

