---
title: "Startup Applications (with root permissions?)"
date: 2010-06-07
forum: General Help
---

### Post by jondecker76 on 2010-06-07
I have a python script I would like to run at at startup. Normally this is pretty easy through System->Preferences->Startup Applications

However, I need this python script to run as root when I start up.  How would I accomplish this?


thanks

---

### Post by bodhi.zazen on 2010-06-07
If you want it to run as root when yo boot, put it it /etc/rc.local or write an init script.

If you want it to run when you log in, add a custom command to the start up applications.

---

