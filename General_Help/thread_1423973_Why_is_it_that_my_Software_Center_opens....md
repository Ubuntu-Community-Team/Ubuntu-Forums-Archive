---
title: "Why is it that my Software Center opens..."
date: 2010-03-07
forum: General Help
---

### Post by jblaven on 2010-03-07
then closes when I try and open it?

The box opens for just a second and then it disappears!  Any ideas on how to fix this?

Thanks,

Joe

---

### Post by sisco311 on 2010-03-07
Open a terminal and run:
```
software-center
```
Post the error message.

---

### Post by Arkitekt on 2010-03-07
Can you please type 'software-center' into terminal and paste anything it outputs back here

---

### Post by shipp on 2010-03-07
I have the same exact problem.  So, I figured I'd post up what my terminal says when I type "software-center."   This all started at the same time, software center opens and then closes immediately.  Songbird says it experienced an unexpected problem and crashes, and Banshee opens a window that displays nothing and then freezes, i get a not responding message.  So, this is what comes up in the terminal:

tshipp@Harold:~$ software-center

(software-center:2985): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:2985): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:2985): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:2985): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:2985): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:2985): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:2985): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:2985): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:2985): GStreamer-WARNING **: adding type gint multiple times

(software-center:2985): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:2985): GStreamer-WARNING **: adding type glong multiple times

(software-center:2985): GStreamer-WARNING **: adding type guint multiple times

(software-center:2985): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:2985): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by shipp on 2010-03-07
1

---

### Post by lavinog on 2010-03-07
Why does software-center use gstreamer???

Try this:
```

sudo apt-get update
sudo apt-get upgrade

```
This should install the latest updates...maybe there is an update that will fix the problem.

---

### Post by shipp on 2010-03-07
Still not working, software center in terminal creates the same stream after updating.  Don't know what the hell is going on, it started doing this after I used software manager to install kdenlive and blender.  Those programs screwed up my songbird and banshee as well.  I think it has something to do with Python or Gstreamer.     Does anyone know if I can just uninstall gstreamer without screwing up more stuff, then reinstall again?

---

### Post by shipp on 2010-03-07
Problem solved: Software center and songbird working fine,  Banshee still will not open, but everything else is good.

Typed
sudo apt-get remove --purge gstreamer0.10-plugins-bad

---

### Post by jblaven on 2010-03-07
OK,

Here is my error!

```
joe@joe-desktop:/$ software-center
/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py:193: Warning: g_param_spec_internal: assertion `(name[0] >= 'A' && name[0] <= 'Z') || (name[0] >= 'a' && name[0] <= 'z')' failed
  from _gst import *

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.

(software-center:3405): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:3405): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:3405): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:3405): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:3405): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:3405): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:3405): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:3405): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:3405): GStreamer-WARNING **: adding type gint multiple times

(software-center:3405): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:3405): GStreamer-WARNING **: adding type glong multiple times

(software-center:3405): GStreamer-WARNING **: adding type guint multiple times

(software-center:3405): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:3405): GStreamer-WARNING **: adding type gulong multiple times
/usr/share/software-center/softwarecenter/apt/aptcache.py:38: Warning: g_param_spec_internal: assertion `(name[0] >= 'A' && name[0] <= 'Z') || (name[0] >= 'a' && name[0] <= 'z')' failed
  gtk.main_iteration()

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
joe@joe-desktop:/$ 

```

---

### Post by jblaven on 2010-03-08
> **shipp said:**
> Problem solved: Software center and songbird working fine,  Banshee still will not open, but everything else is good.

Typed
sudo apt-get remove --purge gstreamer0.10-plugins-bad

Thanks shipp...  that worked for me too.

---

### Post by cartoonhead1970 on 2010-03-24
Thanks that worked for me also.:p

---

### Post by reeboker on 2010-04-03
Hi guys, don't wan't to hack this thread but since I have almost same problem with SC. I would like to ask for help here.

It's just that I can open the software centers window allright, but when I try to instal or remove any software (under user) nothing happens, it's just acting like it doesn't respond to the buttons.

Tried to install wi-fi radar now, here's my log, hope it helps.

":~$ software-center
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:53: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()
WARNING:root:_on_trans_error: org.freedesktop.PolicyKit.Error.NotAuthorized: ('system-bus-name', {'name': ':1.89'}) is not authorized: org.debian.apt.install-packages"

For sudo it's going okay, but for the default user that I've set up in the installation process doesn't work anymore. Any idea what should I do to enable my user to use sc normally.

BTW: This just happened after week or so, before everything was going allright.

---

