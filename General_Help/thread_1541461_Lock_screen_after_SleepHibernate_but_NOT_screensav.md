---
title: "Lock screen after Sleep/Hibernate but NOT screensaver"
date: 2010-07-29
forum: General Help
---

### Post by dave1403 on 2010-07-29
Hi,
running 10.04 Netbook edition.
I would like my screen to lock after the netbook goes to sleep but NOT after it enters the screensaver. is this possible?
i use my laptop to read in the university a lot and to save power tell it to go into black screensaver after a minute of inactivity. if i enable the lock option i have to enter the password each and every time after the black screensaver activates.
but if i deactivate this option and then put the netbook into sleep/hibernate mode it doesn't ask for a password (which i would like)
is there any way configure separate passwords for these instances or are they firmly linked?
any help appreciated
cheers
dave

---

### Post by dave1403 on 2010-07-31
does no one know how to do this?
seriously? i have so far not encountered a single problem im ubuntu that i couldn't solve (with the help of others)
please dont let this be the first!

---

### Post by Jones-K-fin on 2011-01-30
Launch gconf-editor

Go to / > apps > gnome-screensaver
Untick lock_enabled

Worked for my screensaver. More screen lock settings in:

/ > apps > gnome-power-manager > lock


I didn't find much info about this so here it is and I hope this works.

---

