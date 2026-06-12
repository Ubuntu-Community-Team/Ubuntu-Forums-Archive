---
title: "Panel restarts when using certain programs"
date: 2009-11-30
forum: General Help
---

### Post by WeedleTheLiar on 2009-11-30
Recently (I don't know exactly when, probably after the update last week) my network icon in the panel disappeared and was replaced by a second volume icon.  Today I tried to remove one of the volume icons but they both disappeared.  On top of that, when I try to open Rhythmbox it seems like the panel restarts continuously (it will disappear then reappear, taking a decent chunk of system resources each time until I end the process).  Movie Player works fine so I tried using Bluemindo instead but it has the same problem.  ALSA Player works but it sounds like crap unless I set the sound hardware profile to Surround 7.1 (I was using Analog Stereo Output before).

I've tried, one at a time, removing .gnome2, .gconf and .gconfd but no luck.

Please let me know if there are any logs that would be useful and how to get them.

Thanks

---

### Post by WeedleTheLiar on 2009-12-04
These are the messages I get from the terminal

Rhythmbox:
** (rhythmbox:2529): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

Bluemindo:
/usr/share/bluemindo/src/common/functions.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  from md5 import new as md5_new
/usr/share/bluemindo/src/media/gstreamer.py:31: DeprecationWarning: object.__new__() takes no parameters
  cls.ref = super(GStreamer, cls).__new__(cls, args, kws)
Extension `gajim`, registered in *plugins*, could not start.
org.freedesktop.DBus.Error.ServiceUnknown: The name org.gajim.dbus was not provided by any .service files
---------

./bluemindo.py:285: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  'window1', domain='bluemindo')

Does any one know where to go to look up error codes?  I gather (rhythmbox:2529) is an Ubuntu thing, not a Rhythmbox thing.

---

### Post by jegerjensen on 2009-12-04
To me, these errors look like bugs... Especially the error from Rhythmbox. Maybe you should report it as a bug (or preferably two bugs as they may be unrelated)

---

