---
title: "What is causing this to happen Gtk-CRITICAL"
date: 2012-01-07
forum: General Help
---

### Post by bluexrider on 2012-01-07
I have nearly 400,000 lines in my /.xsession-errors that contain
 
(gedit:14637): Gtk-CRITICAL **: IA__gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

the file is nearly 55Mb in size and growing.

Pre-seeding lines before would be:


(gedit:14637): GLib-GObject-WARNING **: value "0" of type `guint' is invalid or out of range for property `tab-width' of type `guint'  (gedit:14637): GLib-GObject-WARNING **: value "0" of type `guint' is invalid or out of range for property `right-margin-position' of type `guint'

no wonder things were slowing down

---

### Post by bluexrider on 2012-01-08
bump

---

### Post by bluexrider on 2012-01-08
closed thread by OP

---

