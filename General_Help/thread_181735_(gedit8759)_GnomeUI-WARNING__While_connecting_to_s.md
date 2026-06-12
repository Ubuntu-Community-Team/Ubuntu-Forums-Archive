---
title: "(gedit:8759): GnomeUI-WARNING **: While connecting to session manager: ?"
date: 2006-05-24
forum: General Help
---

### Post by anxean on 2006-05-24
(gedit:8759): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

If i use sudo or try to open gedit it gives me that, anyone have any ideas?

---

### Post by an.echte.trilingue on 2006-05-24
Use gksu or kdesu instead of sudo when launching root that have a graphical interface.  If you don't you will bugger your home file sooner or later (when sudo even works).

You have to be logged in as a user with admin rights, of course.

---

### Post by giuseppe.dem on 2007-03-22
I noticed that if you put yourself not in the admin group, although you receive the warning
you can use the application (e.g. gedit or kate).
Otherwise, in my case, I am not able to use the application, i.e. the command-line dies out.
Regards
Giuseppe

---

