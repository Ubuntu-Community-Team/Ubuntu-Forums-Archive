---
title: "remote shutdown"
date: 2006-03-13
forum: General Help
---

### Post by Coogan on 2006-03-13
I've got a headless install of Breezy on a small system that I administer thru SSH and FreeNX.  So far I've been unable to do a complete power-down from either; issuing a "shutdown now" command in SSH just shuts down a few services, presumably to make it safe to shut down.  The SSH server doesn't even terminate.

How can I set the system up so that when I issue a shutdown command in SSH it either completely powers down and/or reboots the system?

---

### Post by stuporglue on 2006-03-13
You can do "halt" to power off. I think the 'safer' shutdown version might be "shutdown -h now". The command "reboot" will, of course, reboot your machine. 

Super user privlidges needed for these commands.

---

### Post by _kk on 2006-03-14
**sudo poweroff**

...and it will power off. :)

---

