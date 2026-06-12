---
title: "Adding startup sounds in Xubuntu"
date: 2010-06-11
forum: General Help
---

### Post by winecurmudgeon on 2010-06-11
I found a thread that said GDM doesn't support startup sounds in Xubuntu 10.04, so I only get the tack-ack-ack when the system boots. But is there a workaround or a script that will do the trick?

---

### Post by anglican on 2010-06-11
> **winecurmudgeon said:**
> I found a thread that said GDM doesn't support startup sounds in Xubuntu 10.04, so I only get the tack-ack-ack when the system boots. But is there a workaround or a script that will do the trick?

Well you could get a _login_ sound by adding an autostarted application something like:
```
play /usr/share/sounds/login.wav
```
You'll need to install sox and gnome-audio. Does that do enough?

H

---

### Post by winecurmudgeon on 2010-06-12
That will do it. Thanks for your help.

---

