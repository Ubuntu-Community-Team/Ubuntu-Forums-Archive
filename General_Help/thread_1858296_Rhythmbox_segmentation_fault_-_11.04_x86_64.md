---
title: "Rhythmbox segmentation fault - 11.04 x86_64"
date: 2011-10-12
forum: General Help
---

### Post by anandamide on 2011-10-12
Anyone come across this before / have any tips?

I just re-installed Rhythmbox; now clicking on 'Edit > Preferences' leads to a segmentation fault.

Running from a terminal, the relevant messages seem to be:

```
(rhythmbox:7982): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:7982): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:7982): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': rhythmbox: undefined symbol: menu_proxy_module_load

(rhythmbox:7982): Gtk-WARNING **: Failed to load type module: (null)


(rhythmbox:7982): Rhythmbox-WARNING **: Unable to load encoding profiles from /usr/share/rhythmbox/rhythmbox.gep: no error
Segmentation fault

```

I can fiddle my way around Ubuntu bit break it more often than I fix anything, so the above is largely gobbledigook to me. Any ideas on what's going wrong and / or how to fix it?

Cheers :-)

---

### Post by firestormxvii on 2011-10-22
I have the same issue. I've tried playing with the /usr/share/rhythmbox/rhythmbox.gep file but the same behavior happens.

Is there another way to edit these settings? ~/.local/share/rhythmbox/rhythmdb.xml just looks like it has the metadata for the songs in my library.

---

