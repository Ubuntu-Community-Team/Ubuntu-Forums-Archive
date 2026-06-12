---
title: "need to emulate center button on 11.04 using fluxbox"
date: 2011-09-20
forum: General Help
---

### Post by mathog on 2011-09-20
I have an old laptop with a trackpad and two mouse buttons.  It is running fluxbox because it is far too wimpy for gnome or kde.  It needs to be able to emulate the center mouse button.  Unfortunately the helpful software seems to be hellbent on not doing so.

Set up an xorg.conf, put in

 ```
 Option "Emulate3Buttons" "true"

```
restarted X11, and Xorg.0.log showed:

```
(WW) Hotplugging is on, devices using drivers 'kbd', 'mouse', or 'vmmouse' will be disabled.
(WW) Disabling Mouse!

```
3 button emulation was not working (verified in xev).  Further on in that log file it said:

```
(--) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: configuring as mouse
(II) XINPUT:  Adding extended input device "TPPS/2 IBM Trackpoint" (type: MOUSE).

```
First of all, there are not 3 buttons, just two sets of L/R buttons, the trackpad, and a joystick.  (The Joystick does not click).

So it looks like xorg.conf is useless.  Then I tried  gpointing-device-settings.  That let me turn on center button emulation.  However, it didn't stick between X11 restarts.  Bizarrely, on the next restart g-d-s still showed that the center button emulation was on, but it wasn't.  It was possible to bring it back by running g-d-s, disabling center button emulation, OK. Run it again, enable, OK.

It looks to me like a permanent xinput setting has to be stored somewhere.  Any idea what that setting might be and where to place it?

Thank you.

---

### Post by mathog on 2011-09-21
This works:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#xorg.conf.d)

now if I can just get syndaemon working.  Tried putting

  Option "SHMConfig" "on"

in that file, and restarting the X11 server, but syndaemon just exits without leaving a message anywhere.  That is just the same as before that option was added.  Maybe it doesn't work with the trackpoint?

---

