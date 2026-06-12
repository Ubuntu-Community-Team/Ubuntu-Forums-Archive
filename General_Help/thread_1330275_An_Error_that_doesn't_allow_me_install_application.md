---
title: "An Error that doesn't allow me install application or update my system"
date: 2009-11-18
forum: General Help
---

### Post by Dark Sorrow on 2009-11-18
I installed Ubuntu using in Windows Installer.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Whenever i run the command **dpkg --configure -a** i get not enough permission error.

---

### Post by drs305 on 2009-11-18
run it like this:
```

sudo dpkg --configure -a

```

When asked for your password, type it and press ENTER. You won't see anything as you type.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Dark Sorrow on 2009-11-18
> **drs305 said:**
> run it like this:
```

sudo dpkg --configure -a

```

When asked for your password, type it and press ENTER. You won't see anything as you type.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

Can this humble soal ask why such error occured so that next time i can avoid it.

---

### Post by drs305 on 2009-11-18
> **Dark Sorrow said:**
> Can this humble soal ask why such error occured so that next time i can avoid it.

Normally it is caused by an interrupted installation. If you were doing the install via command line or you had the "details" viewable during the Update Manager you may have been able to see what happened.

After the fact, you could *try* to go through the system logs. In Jaunty, System, Administration, System Log. If you don't see dpkg.log, you can File, Open, (/var/log/) dpkg.log.  It would not necessarily be easy to find where the error occurred and probably would be more trouble than it's worth, but that's where you might find the answer if you are really interested.

---

