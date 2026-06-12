---
title: "Unable to remove Firestarter from startup"
date: 2009-07-23
forum: General Help
---

### Post by Brummy137 on 2009-07-23
I added Firestarter to my startup through sessions (8.04 LTS3).  This is before I learned it was not necessary to do this in order to have the firewall working.  Now I'd really like to remove it from my start-up  because I used gksudo and I always get the authorization box to pop up right when I log into the desktop environment.

In my attempt to remove firestarter I went into sessions disabled it, and then removed the entry.  This didn't remove firestarter from my start-up.  I attempted to remember my session without firestarter running, but this didn't work either.  

Is there some configuration file I can modify that will allow me to remove firestarter once and for all from my start-up programs?  I don't seem to be able to solve my problem using the sessions GUI.

---

### Post by JOHNNYG713 on 2009-07-23
Go to add and remove programs and remove firestarter ,if you still want the option to run it, after un-installing, reinstall

---

### Post by doas777 on 2009-07-23
on the second tab in the Sessions applet, is the box checked to remember session applications? if so, just exit firestarter before shutting down. if it isn't in the startup apps anymroe, then it should stop trying to load at login.

---

### Post by wojox on 2009-07-23
Or if you have a third tab Startup Programs delete it from there.

---

### Post by Brummy137 on 2009-07-23
Uninstalling firestarter stopped this vicious cycle.  Thanks for all the help folks.

---

