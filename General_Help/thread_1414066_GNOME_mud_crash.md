---
title: "GNOME mud crash"
date: 2010-02-23
forum: General Help
---

### Post by efranor on 2010-02-23
After i start up gnome-mud it crashes, so I ran debug and got this:

efranor@efranor-laptop:~$ gnome-mud --debug

(gnome-mud:3504): GVFS-RemoteVolumeMonitor-WARNING **: cannot open directory /usr/share/gvfs/remote-volume-monitors: Error opening directory '/usr/share/gvfs/remote-volume-monitors': No such file or directory

(gnome-mud:3504): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gnome-mud:3504): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gnome-mud:3504): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-mud:3504): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault

---

