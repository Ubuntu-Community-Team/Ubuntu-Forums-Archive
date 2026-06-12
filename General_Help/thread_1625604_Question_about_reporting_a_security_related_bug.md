---
title: "Question about reporting a security related bug"
date: 2010-11-19
forum: General Help
---

### Post by taylorkh on 2010-11-19
Someone please refresh my memory... I just reported a bug involving escalated privileges without proper authentication to launchpad/ubuntu.  I seem to remember that when I did this some years ago there was a way to flag the bug as security related. I do not find such an option on launchpad - perhaps the old bug was for a different distro.

Please advise - I would like to get this bug routed to the correct folks.

TIA,

Ken

---

### Post by WorMzy on 2010-11-19
If it was a sudo bug, report it here: [http://www.sudo.ws/sudo/bugs/](http://www.sudo.ws/sudo/bugs/)
If it was a su bug, report it to [email]bug-coreutils@gnu.org[/email]

If it was a bug in another app, check it's man page for details on how to report bugs to the proper place.

---

### Post by taylorkh on 2010-11-19
Thanks WorMzy,

It appears at first glance to be a bug in shares-admin (part of gnome-system-tools) although further testing seems to implicate VMWare. I can reproduce the issue in guest VMs but not on a physical machine. I am rebuilding the physical machine to get a cleaner test.  I have the bug charged against gnome-system-tools.  

Ken

---

### Post by WorMzy on 2010-11-19
If you manage to confirm it, or replicate it, then report it on here: [https://bugzilla.gnome.org/](https://bugzilla.gnome.org/)

It's much more likely to get noticed on there by the GNOME developers than on Launchpad.

---

