---
title: "Problems with Gnome3"
date: 2011-12-04
forum: General Help
---

### Post by BobvanderPoel on 2011-12-04
Okay, this is Bob. I'm hoping that this will help trace it down ... and I'm using Ubuntu, not a derivative.

Kernel  3.0.0-14-generic-pae

Yes, 11.10

32 bit

Installed as a update to 11.04

Other than the fact that I hate Gnome 3 ... seems to be okay :) I'm spending 99% of my time in xfce4. But, the problem with mahjongg and others is present in kde, xfce4 and gnome.

Reproduces all the time. Worked perfectly in 11.04.

The only thing I have not had time to try is to disable nvidia and see if the noveau (??) drivers make a difference.

---

### Post by BobvanderPoel on 2011-12-04
I have no idea how to disable nvidia :( So, if someone wants me to try that ... I'll need help.

I just ran mahjongg from a command line. I get screenfulls of messages, but they all appear to be one of the following:

```

bob$ mahjongg

(mahjongg:2735): Gtk-WARNING **: Error loading theme icon 'scores' for stock: Icon 'scores' not present in theme

(mahjongg:2735): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(mahjongg:2735): Gtk-CRITICAL **: gtk_theming_engine_render_icon_pixbuf: assertion `base_pixbuf != NULL' failed

```

Hopefully this is helpful.

---

### Post by CharlesA on 2011-12-04
Moved to own thread.

---

