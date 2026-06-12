---
title: "BIG Problem with Firefox. I mean, BIG!"
date: 2006-01-30
forum: General Help
---

### Post by Rev. Nathan on 2006-01-30
I'm having some serious problems with firefox. I don't know what triggered it, or how to fix it. Usually firefox opens up fullscreen, as a browser should. But today, it opened up at a very odd, annoying, unbrowsable angle. Ignoring that, I browsed on and tried to search using the search bar. All my engines were gone! Then, when trying to download and recover them all, I noticed, yet again, I could not download any!

So I restarted, reinstalled, etc. And now that I reinstalled firefox, it opens up all stupidly, **and** I have no plugins, no skins, no searches, no fun!

What am I to do?

---

### Post by RAOF on 2006-01-30
Something's probably screwy in your user profile.  I'd suggest renaming the ~/.mozilla directory (run mv ~/.mozilla ~/.mozilla-backup) and then starting firefox again.  It should start up with a pristine new user profile, and work :)

---

### Post by kingsidy on 2006-01-30
delete it complete if you are using 1.5. if not then upgrade to 1.5. make sure you delete the hidden folder in your home directory (.firefox if you are using firefox 1.5). i am currently using 1.5.0.1RC1. make sure you also delete the folder in opt directory if you are using 1.5, and replace it.

---

### Post by aysiu on 2006-01-30
[QUOTE=kingsidy]make sure you delete the hidden folder in your home directory (.firefox if you are using firefox 1.5).[/QUOTE] I'm using 1.5 right now, and the folder's called .mozilla, not .firefox.

---

### Post by Rev. Nathan on 2006-01-30
OK, I deleted .mozilla and removed it from apt. Now, it seems to be working. I guess I am just disappointed that it had to go fail on me so oddly.

---

### Post by kingsidy on 2006-01-30
never had a problem with it though. although once the tabbed browsing extension was making my firefox 1.0.7 behave really funny. i though it was messed up until i uninstalled the application and it went back to normal. it is not perfect by all means.

---

