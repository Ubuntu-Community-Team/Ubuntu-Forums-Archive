---
title: "Problem after install Gtk 2.18"
date: 2009-11-06
forum: General Help
---

### Post by meshgrid on 2009-11-06
Greeting all,
I use ubuntu 8.04. Its use gtk 2.10 by default. To day i want to try new application, but its need newer gtk. So i download gtk 2.18, glib 2.22 and pango 1.26.

I compile and install all in my custom path /opt/custom/usr/local
Everything is OK (i have set LD_LIBRARY_PATH, PKG_CONFIG_PATH).

And then i compile giggle (git frint end), but its raise fatal error :

[FONT=Courier New](lt-giggle:11561): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(lt-giggle:11561): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
**
Pango:ERROR:pangofc-fontmap.c:2134:pango_fc_font_description_from_pattern: assertion failed: (res == FcResultMatch)
Aborted


Anyone know what's wrong ??

Sorry for my bad english and thanks
[/FONT]

---

