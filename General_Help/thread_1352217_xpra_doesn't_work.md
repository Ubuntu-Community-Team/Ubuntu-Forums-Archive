---
title: "xpra doesn't work"
date: 2009-12-11
forum: General Help
---

### Post by sdhawley on 2009-12-11
**xpra doesn't work**
sdhawley@freedom:~$ xpra start :42
Entering daemon mode; any further errors will be reported to:
  /home/sdhawley/.xpra/:42.log
sdhawley@freedom:~$ export DISPLAY=42
sdhawley@freedom:~$ gcalctool

(gcalctool:4071): Gtk-WARNING **: cannot open display: 42
sdhawley@freedom:~$ xpra stop :42
xpra at :42 has exited.
sdhawley@freedom:~$ xpra list
Found the following xpra sessions:
    DEAD session at :42 (cleaned up)
sdhawley@freedom:~$ 

**log file**

dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.66" is not allowed to own the service "org.x.config.display42" due to security policies in the configuration file)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.66" is not allowed to own the service "org.x.config.display42" due to security policies in the configuration file)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
Xlib:  extension "RANDR" missing on display ":42.0".
Xlib:  extension "RANDR" missing on display ":42.0".
/usr/lib/python2.6/dist-packages/wimpiggy/wm.py:9: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
Xlib:  extension "RANDR" missing on display ":42.0".
New connection received
Handshake complete; enabling connection
Sorry, this pre-release server only works with clients of exactly the same version (v0.0.6)
Shutting down in response to request

**All help appreciated **

---

### Post by tron1point0 on 2010-05-01
export DISPLAY=:42

The colon is important :)

---

