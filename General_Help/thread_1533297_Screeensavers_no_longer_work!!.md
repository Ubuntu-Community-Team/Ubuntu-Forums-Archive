---
title: "Screeensavers no longer work!!"
date: 2010-07-17
forum: General Help
---

### Post by Cfhs_1 on 2010-07-17
Hello everyone. I have a annoying problem, my screensavers in ubuntu 10.04 no longer work. When the screensaver is supposed to activate all I get is a blank screen. This started happening after I installed xscreensaver and copied all of it's 200+ screensavers over to to gnome-screensaver's directory. I have since removed xscreensaver. I have tried multiple screensavers, old and new, reinstalling xscreensaver, and reinstalling gnome-screensaver to no avail. Not even locking the screen will make the screensaver function properly, although I can preview the screensavers. Can someone please help me?

Thanks,
Cfhs_1

---

### Post by Cfhs_1 on 2010-07-17
Okay, so I fixed it myself by deleting the screensavers folder at /usr/share/applications/screensaver then rebooting, and letting gnome-screensaver rewrite the files (It did this automatically.) Then I copied over only the screensavers i wanted from the xscreensaver folder located at /usr/lib/xscreensaver. Problem solved.:popcorn:

---

