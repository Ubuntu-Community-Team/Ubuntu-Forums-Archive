---
title: "apply gedit styles using gnome 3"
date: 2011-10-13
forum: General Help
---

### Post by GrandVizier on 2011-10-13
I created some custom syntax highlighting for error logs in my previous version on Ubuntu, but now that I have installed Gnome 3 (using 11.04), the styles are not having an effect

I put a copy of my .lang file in both paths
```
/usr/share/gtksourceview-3.0/language-specs/
/usr/share/gtksourceview-2.0/language-specs/
```

---

### Post by crdlb on 2011-10-13
Do you get any output if you run gedit in a terminal? You need to close all gedit windows, otherwise the existing instance will be used. What versions are gedit and libgtksourceview-3.0-0?

---

### Post by GrandVizier on 2011-10-13
```
(gedit:22821): GLib-WARNING **: XDG_RUNTIME_DIR variable not set.  Falling back to XDG cache dir.
`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:22821): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': gedit: undefined symbol: menu_proxy_module_load

(gedit:22821): Gtk-WARNING **: Failed to load type module: (null)
```
those last 2 lines repeat themselves several times

gedit: 3.0.6-0
libgtksourceview-3.0-0: 3.0.5-0

---

### Post by GrandVizier on 2011-10-13
huh, it's suddenly working...

(though the classic color scheme for gedit is definitely not suitable, but that's a different issue)

---

