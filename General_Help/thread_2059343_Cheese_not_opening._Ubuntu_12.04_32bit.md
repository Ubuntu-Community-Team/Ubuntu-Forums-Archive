---
title: "Cheese not opening. Ubuntu 12.04 32bit"
date: 2012-09-17
forum: General Help
---

### Post by BrutalHesher on 2012-09-17
I am running Ubuntu 12.04 32bit on a Asus U43F i5 m480 2.67ghz.

I am a total n00b and should be helped like speaking to a small child. Heres the problem, I have installed Cheese and it will not run. When running from terminal this is what happens.



wintermute@wintermute-U43F:~$ cheese

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:15113): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
libv4l2: error getting pixformat: Invalid argument

** (cheese:15113): CRITICAL **: cheese_camera_device_get_uuid: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed
Segmentation fault (core dumped)


what do?

---

### Post by Kirk Schnable on 2012-09-17
First of all, even though it's tempting, don't be distracted by the Gtk-WARNING errors.  They are probably normal.

The last line with the CRITICAL error is the problem.

Unfortunately, it looks like there's a bug open on Launchpad about this, with no solution as of yet.
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930128](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930128)

I saw another thread about this on the Ubuntu forums, but their solution was hardly a "solution":
[http://ubuntuforums.org/showthread.php?t=1969336](http://ubuntuforums.org/showthread.php?t=1969336)

If I find anything else out, I'll be sure to let you know...

Cheers
Kirk

---

### Post by BrutalHesher on 2012-09-18
> **Kirk Schnable said:**
> First of all, even though it's tempting, don't be distracted by the Gtk-WARNING errors.  They are probably normal.

The last line with the CRITICAL error is the problem.

Unfortunately, it looks like there's a bug open on Launchpad about this, with no solution as of yet.
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930128](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930128)

I saw another thread about this on the Ubuntu forums, but their solution was hardly a "solution":
[http://ubuntuforums.org/showthread.php?t=1969336](http://ubuntuforums.org/showthread.php?t=1969336)

If I find anything else out, I'll be sure to let you know...

Cheers
Kirk



Thank you,I will be sure to keep my eye on these threads. Cheers!

---

