---
title: "How do I get dIfferent themes for different applications?"
date: 2010-06-13
forum: General Help
---

### Post by Kep on 2010-06-13
I've heard that it's possible to get different themes for different applications. How does one do this?

---

### Post by limestone on 2010-06-13
Never heard of...??? It's possible if you're using both Gtk apps and Qt apps.

---

### Post by VCoolio on 2010-06-13
You can do so by specifying the GTK2_RC_FILES variable either in a terminal command, or in the menu, or in the Exec= line in the .desktop file you may find in /usr/share/applications, /usr/local/share/applications or ~/.local/share/applications. Like this to use Human for openoffice:
```
GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc openoffice.org3 -writer
```

---

