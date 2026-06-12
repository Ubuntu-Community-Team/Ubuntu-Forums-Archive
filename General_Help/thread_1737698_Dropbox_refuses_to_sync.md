---
title: "Dropbox refuses to sync"
date: 2011-04-23
forum: General Help
---

### Post by noper2 on 2011-04-23
I'm running Ubuntu 10.10, and until yesterday dropbox worked perfectly. Suddenly, it no longer wants to sync -- the icon doesn't appear, and attempting to run it from the command line just opens up my dropbox folder. I've tried all the commands listed in the man page, and always get the same result. 

Running the dropbox script in /usr/bin, I simply get the error message "Dropbox isn't responding". 

Has anyone else experienced this?


EDIT:Okay, whatever it was, it was fixed either in an update or by magic.

---

### Post by SecretCode on 2011-04-24
fwiw, I also sometimes find that Dropbox is not syncing (but the icon is still visible - though just the blue box, none of the usual overlays). Stopping Dropbox (from the right-click menu on the notification icon) and restarting it has so far always sorted it out.

You also need to restart Nautilus if the **nautilus-dropbox** package is updated.

---

