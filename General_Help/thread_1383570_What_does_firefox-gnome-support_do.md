---
title: "What does firefox-gnome-support do?"
date: 2010-01-17
forum: General Help
---

### Post by narr on 2010-01-17
On my Xfce box, it took me about 4 hours today to figure out why I could not change the filebrowser in Firefox, which is invoked by right-clicking on a download list item and selecting "open containing folder". 

Well, it turned out that because of my parallel Gnome installation there is a (meta) package called firefox-gnome-support (which depends on firefox-3.5-gnome-support and xulrunner-1.9.1-gnome-support) and well, then it just opens Nautilus. So now I'd like to know which behaviour of firefox is changed by firefox-gnome-support. On the Xfce forums there are often reports about some strange firefox behaviour and I'm curious if/to what extend these could be caused by this package :)

---

### Post by kWahab on 2010-01-20
You probably already read this but here it is anyway...

From [http://packages.ubuntu.com/karmic/firefox-3.5-gnome-support](http://packages.ubuntu.com/karmic/firefox-3.5-gnome-support)

Support for Gnome in Mozilla Firefox

This is an extension to Firefox that allows it to use protocol handlers from GnomeVFS, such as smb or sftp, and other GNOME integration features. 

Marked as security... ????

A fresh xubuntu system also has this package installed by default.

?Didn't they ditch GnomeVFS long ago? gvfs replaced it.

---

