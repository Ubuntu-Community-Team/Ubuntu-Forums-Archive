---
title: "Adding wm to GDM?"
date: 2004-10-23
forum: General Help
---

### Post by ohman on 2004-10-23
Simple enough, Id like to add Fluxbox to the gdm sessions menu, but /etc/gdm/Sessions doesn't exist.  What can I say?  I want the eye candy of flux and X.org 6.8.1 :)

---

### Post by renato on 2004-10-23
Create a file called .xsession in your home directory
add these two lines:

xscreensaver -no-splash &
fluxbox


xscreensaver is not necessary but this way you can start it automatically at log-in.

Then from GDM choose "default session" or somethnig like that (My version is in Italian)

TIP:
If fonts of Gnome applications are too small from other WMs, create a file in your home directory and call it .gtkrc-2.0
then add this line:

gtk-font-name = "Helvetica 12"

---

