---
title: "Update broke my Xserver with VIA Unichrome IGP"
date: 2009-08-05
forum: General Help
---

### Post by theBishop on 2009-08-05
I have a junker PC I'm using as a server.  It's got a VIA/S3 Unichrome K8N800 IGP card which is detected perfectly in the Jaunty LiveCD.  

But sometime in the last month or so an update must have broke support.  I rarely reboot, so I don't know exactly when it happened.  

In a nutshell, the screen goes either flat black or flat white and the keyboard/mouse are unresponsive.  I am able to connect over SSH, there isn't any file loss or anything.  

Here are some of my relevant logs/configs:

[B]/var/log/gdm/:0.log:
[/B][http://pastebin.ca/1519386](http://pastebin.ca/1519386)

**lspci:**
[http://pastebin.ca/1519387](http://pastebin.ca/1519387)
[B]
/var/log/Xorg.0.log:[/B]
[http://pastebin.ca/1519388](http://pastebin.ca/1519388)

---

### Post by theBishop on 2009-08-05
It looks like the "via" kernel module may not be included anymore.  Using "openchrome" gives me weird-looking blue characters on the screen.

---

