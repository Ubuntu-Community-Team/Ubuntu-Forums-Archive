---
title: "Synaptic will not open"
date: 2006-03-27
forum: General Help
---

### Post by Rumor on 2006-03-27
Greeetings: 
I cannot open Synaptic Package Manager either from the menu or the CLI. I get this error when trying from the command prompt (opening as sudo)

```
(synaptic:9540): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure:
assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9540): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: 
assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault

```

Any ideas?

---

### Post by Rumor on 2006-03-28
[QUOTE=Rumor]Any ideas?[/QUOTE]

Yes, try this:

```
sudo apt-get install -f
```

---

### Post by Rumor on 2006-03-28
[QUOTE=Rumor]Yes, try this:

```
sudo apt-get install -f
```[/QUOTE]

Hey, thanks! That did the trick!

---

