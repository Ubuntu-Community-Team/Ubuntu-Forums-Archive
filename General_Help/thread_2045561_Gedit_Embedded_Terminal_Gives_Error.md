---
title: "Gedit Embedded Terminal Gives Error"
date: 2012-08-21
forum: General Help
---

### Post by UnknownDiety on 2012-08-21
I'm using Ubuntu 12.04. I've installed the gedit-plugins, but whenever I open gedit and go to preferences and then click the check box to enable the embedded Terminal I receive an error.

Also I was wondering if there was anyway to change the colors of the embedded terminal since the preferences button for it in the plugin menu is disabled.

```
(gedit:3773): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION (selection)' failed
corruption@corruption:~/Desktop/Python$ gedit & disown
[1] 3836
corruption@corruption:~/Desktop/Python$ 
(gedit:3836): Gtk-CRITICAL **: gtk_accessible_get_widget: assertion `GTK_IS_ACCESSIBLE (accessible)' failed

(gedit:3836): Gtk-CRITICAL **: gtk_accessible_get_widget: assertion `GTK_IS_ACCESSIBLE (accessible)' failed

(gedit:3836): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gedit:3836): Gtk-CRITICAL **: gtk_accessible_get_widget: assertion `GTK_IS_ACCESSIBLE (accessible)' failed

(gedit:3836): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_IS_TREE_SELECTION (selection)' failed
```

---

