---
title: "Mono: cannot find gdk-x11-2.0"
date: 2006-06-16
forum: General Help
---

### Post by traherom on 2006-06-16
I get this error when attempting to run some mono programs, such as the wallpaper changer someone mentioned in [this thread](http://www.ubuntuforums.org/showthread.php?t=49336&highlight=wallpaper+mono).
> Unhandled Exception: System.DllNotFoundException: gdk-x11-2.0
in (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)
in [0x00018] (at /home/ryan/src/rbr/traylib.cs:35) Egg.TrayIcon:OnRealized ()
in <0x00036> Gtk.Widget:realized_cb (IntPtr widget)
in (wrapper native-to-managed) Gtk.Widget:realized_cb (intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Widget:gtk_widget_show_all (intptr)
in <0x00017> Gtk.Widget:ShowAll ()
in [0x0004d] (at /home/ryan/src/rbr/Main.cs:35) rbr.MainClass:.ctor ()
in [0x00005] (at /home/ryan/src/rbr/Main.cs:16) rbr.MainClass:Main (System.String[] args)

A quick "locate gdk-x11-2.0" shows me that the library is at /usr/lib/libgdk-x11-2.0.so.0, so I don't think I need to install anything... for some reason mono just doesn't see it. Er... any ideas?

---

### Post by wlvs on 2007-02-25
I ran sudo ln -s /usr/lib/libgdk-x11-2.0.so.0 /usr/lib/libgdk-x11-2.0.so and now every program that through up these errors seem to work fine.  Hope this helps,
Tom

---

### Post by traherom on 2007-02-26
> **wlvs said:**
> I ran sudo ln -s /usr/lib/libgdk-x11-2.0.so.0 /usr/lib/libgdk-x11-2.0.so and now every program that through up these errors seem to work fine.  Hope this helps,
TomThanks! That fixed it. :)

---

