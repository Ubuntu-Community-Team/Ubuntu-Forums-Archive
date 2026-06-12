---
title: "Can't get Jupiter to work in Xubuntu 11.10"
date: 2011-10-22
forum: General Help
---

### Post by scottbomb on 2011-10-22
After installing, I get a pop-up that tells me it has whitelisted itself to the sys tray and I need to log out and back in to see it. I logged out, back in, and it's still not in the sys tray but I get the same pop-up notification. I even re-booted and it happened again. Any ideas?

I thought maybe I'd try to manually whitelist it. I've googled the heck out of this and can't find any information about whitelisting all apps in XFCE. Everything I find relates to Unity.

---

### Post by gsmanners on 2011-10-22
I'm sure you know [where]("https://launchpad.net/~webupd8team") to go. :D

---

### Post by Rodney9 on 2011-10-22
The pop-up shows every time I start Xubuntu as well, but Jupiter is running with it's icon in the top panel, so I just ignore the pop-up, it goes away after a few seconds.

---

### Post by scottbomb on 2011-10-22
I don't see it there. Supposed to be a lightning bolt, right? 

I uninstalled and reinstalled Jupiter, logged out and back in, still not there. I went to panel -> add new items, and it's not in the list of available plugins.

> **gsmanners said:**
> I'm sure you know [where]("https://launchpad.net/~webupd8team") to go. :D

I'll do some looking over there, thanks.

---

### Post by scottbomb on 2011-10-22
I finally found the answer in the comments section on this page:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

Apparently, the program requires libmono-posix 4.0, which is not included in Xubuntu by default. I installed it from Synaptic and now it works.

---

