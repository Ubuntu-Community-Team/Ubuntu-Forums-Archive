---
title: "cannot set up dual monitors in ubuntu 12.04"
date: 2012-08-27
forum: General Help
---

### Post by deli6z on 2012-08-27
after I upgraded to 12.04 my dual monitors stopped to work. after I try to set it up id Settings/Display I get error:

The selected configuration for displays could not be applied: required virtual size does not fit available size: requested=(3840, 1080), minimum=(320, 200), maximum=(1920, 1920)

Failed to apply configuration: %s GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(3840, 1080), minimum=(320, 200), maximum=(1920, 1920)

If I try to edit it in AMD catalyst control center (I run this command gksu amdcccle) I get this:

(process:2955): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:2955): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.3/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:2955): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:2955): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

Tried to restore xorg.conf many times and start over but did not help. I have Ati Radeon HD 3450 video card and ATI/AMD proprietary FGLRX driver installed.

Thanks you the help.

---

