---
title: "gnome-panel won't start"
date: 2012-01-09
forum: General Help
---

### Post by DJ . on 2012-01-09
I installed gnome-panel again, and it won't start. I ran it threw terminal and got this:
```


(gnome-panel:6951): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnome-panel:6951): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0x1c9f9e0'
Floating point exception
```What does this mean and how can I fix it? It was working before. Running Ubuntu 11.10 64 bit on an Acer Aspire 5532

---

### Post by DJ . on 2012-01-09
I noticed a /build folder in that message, but I have no /build folder. Is it in the gnome-panel folder (wherever that may be)? Could it be something in there messing with it?

---

### Post by DJ . on 2012-01-09
Seems it works fine as root...
It's something wrong with one of my panels then. Where can I find panels specifically to my default user?

---

### Post by DJ . on 2012-01-09
I'm convinced that it's something I put on the panel, I tried running
```
gconftool-2 --get /apps/panel/general/object_id_list
```but it just spit out a "No value set" error
What do I do? Please help, I don't want to go back to Unity!

EDIT:Solved! It was something in my panel. I logged out, logged back in and gnome-panel was open. I quickly removed the "window list" and now it works!

---

