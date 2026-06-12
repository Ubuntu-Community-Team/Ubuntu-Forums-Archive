---
title: "I didn't touch it.... - gedit being odd"
date: 2006-04-13
forum: General Help
---

### Post by PriceChild on 2006-04-13
```
pricechild@thebeast:/boot/grub$ sudo gedit menu.lst

** (gedit:15863): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

(gedit:15863): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:15863): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:15863): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:15863): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:15863): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

** (gedit:15863): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:15863): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:15863): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:15863): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

```

Help... without the "sudo" it works fine, just read only.

This never happenned before, sudo has been very strange since an update a day or two ago.

Pricey

---

### Post by enopepsoo on 2006-04-14
try a sudo apt-get update / upgrade and see if that fixes it?

---

### Post by PriceChild on 2006-04-14
didn't do anything.

-UPDATE-

It's doing the same when i edit other files such as when trying to edit my ut script.

---

### Post by PriceChild on 2006-04-14
My system is being a bit wierd... trying to open a root nautilus, or even running the ut uninstall script frmo nautilus choosing "run in terminal" causes a black terminal to appear, and not do anything at all...

Anyone think i should just backup everything and do a complete reinstall?

---

### Post by PriceChild on 2006-04-14
sorry about this but *bump*

---

