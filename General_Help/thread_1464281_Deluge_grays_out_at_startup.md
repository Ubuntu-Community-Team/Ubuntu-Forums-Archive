---
title: "Deluge grays out at startup"
date: 2010-04-28
forum: General Help
---

### Post by whalogreg on 2010-04-28
Recently, Deluge has not been starting up for me. The Window opens, but remains completely blank, and then grays out (as if unresponsive). I tried running it from terminal and got this in return..

```

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(deluge:21099): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",
1.1.9
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/statusbar.py:109: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
Killed

```

Any ideas how to resolve this?

Thanks

---

### Post by 2hot6ft2 on 2010-04-28
Have you tried changing the theme you're using?

---

### Post by whalogreg on 2010-05-08
Upgrade to 10.04 cured it...

---

