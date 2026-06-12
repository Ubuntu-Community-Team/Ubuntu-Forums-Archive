---
title: "USB hard drives not mounting after suspend"
date: 2011-07-19
forum: General Help
---

### Post by sinfony on 2011-07-19
I've taken to putting my server to sleep when I won't be using it for a while via pm-suspend. However, when I resume the machine (by wake on LAN), two out of my three USB hard drives are not remounted. After poking around on the web for a while trying to figure out why this is happening, I'm at a loss. What could be causing this issue? What do I need to do to resolve it? If it's relevant, I'm running 11.04 but had same issue under 10.10, and I almost exclusively access the machine via SSH.

---

### Post by trollolo on 2011-07-19
I know that, at least for me, I had to re-set my network connections after coming out of a hibernation/suspended state. I'd have to open up the network manager, click on my network, be told that i had been disconnected, wait for it to "re-find" my network, then reselect it. 
 
Got to be very annoying, I guess this could be what you're having, since from what I know, SSH has to do with wirless nonesense.

---

### Post by sinfony on 2011-07-21
Networking is fine after resume. As far as I can tell, everything is working normally after resume except these two hard drives.

---

