---
title: "Error in terminal Gtk-Message: Failed to load module &quot;pk-gtk-module&quot;: libpk-gtk-modul"
date: 2010-07-19
forum: General Help
---

### Post by soldier1st on 2010-07-19
hi when i type in a command(any) i get this error Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory

what dees this mean?Thnx

---

### Post by LeeDaugherty on 2010-07-20
I believe you have encoutered the known packagekit bug #389766.  A temporary fix is changing the key in gconf-editor /apps/gnome_settings_daemon/gtk-modules/pk-gtk-module  to false.

---

### Post by soldier1st on 2010-07-20
that fixed it thanks.

---

