---
title: "Controling daemons start"
date: 2010-08-20
forum: General Help
---

### Post by felix-leg on 2010-08-20
A few days ago I installed some new services which now runs automatically after each system's start. By default it is a good behavior, but in my case I wish to run them manually, only when desired. Where to switch off auto-start?

---

### Post by hal8000 on 2010-08-20
Try system, preferences, startup applications, this is where your app may be started from.


If not, post back as its either added to the runlevel or starting in /etc/init.d/rc.local

---

### Post by felix-leg on 2010-08-20
> **hal8000 said:**
> Try system, preferences, startup applications, this is where your app may be started from.
That's where I've started looking for.

---

