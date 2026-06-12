---
title: "Some Gnome apps cannot live together!"
date: 2009-11-15
forum: General Help
---

### Post by Darktrax on 2009-11-15
Its System Monitor 2.28.0 - one of the applications in the Panel menu of Karmic, that shows CPU usage, memory, etc. This display is instantly trashed whenever the calculator (galculator v1.3.4) application is started. Galculator is a GTK2-based scientific calculator.

Also - when the calculator is running, any attempt to run "System Monitor" is doomed. The display flashes on for an instant, and then quits.

I should mention that galculator is not the default one (gcalctool 5.28.1) I use galculator because it offers reverse Polish entry format. Other things I notice is that the galculator entry in the Applications -> Accessories menu does not have an icon.

When I start galculator fropm a terminal, it runs OK, but the terminal message says..```

:~$ galculator 

(galculator:3423): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(galculator:3423): Gdk-CRITICAL **: gdk_window_set_icon_list: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(galculator:3423): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(galculator:3423): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
```I don't know any of what might be going on here. Either app seems to work fine provided the other is not present. It is a bit of a worry though. There are some important applications I would not want to have quit, just because another got started! Should I stop using galculator?  :|

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
Confirmed... system monitor will not stay open when galculator is opened. It might be a good idea to submit a bug.

---

### Post by Darktrax on 2009-11-16
> **Sin@Sin-Sacrifice said:**
> Confirmed... system monitor will not stay open when galculator is opened. It might be a good idea to submit a bug.

Thanks for the checkout. Gosh - my first "proper" bug, meaning "one that does not involve any of my own fumbles".

---

