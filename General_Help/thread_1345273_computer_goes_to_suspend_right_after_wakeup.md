---
title: "computer goes to suspend right after wakeup"
date: 2009-12-03
forum: General Help
---

### Post by m4lte on 2009-12-03
Hey, 
I'm running 9.10 on my laptop. Occasionally, when the computer wakes up from suspend it's just active for a few seconds and then goes back to suspend.
Any ideas how this could happen? Are there any log files where I can find relevant information?

cheers!

---

### Post by aysiu on 2009-12-05
Could be this bug:
[https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411](https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411)

---

### Post by m4lte on 2010-01-07
I solved the problem setting one key in gconf:


Run gconf-editor and go to

/ --> apps --> gnome-power-manager --> actions

and uncheck the box labeled "event_when_closed_battery".

---

