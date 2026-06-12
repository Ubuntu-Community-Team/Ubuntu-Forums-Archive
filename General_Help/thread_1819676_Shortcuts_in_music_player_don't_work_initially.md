---
title: "Shortcuts in music player don't work initially"
date: 2011-08-06
forum: General Help
---

### Post by fizikz on 2011-08-06
When I start clementine, I always get the following error messages in
the terminal:

virtual bool QxtGlobalShortcutBackend::DoRegister()
QxtGlobalShortcut failed to register: "Media Next"
QxtGlobalShortcut failed to register: "Media Play"
QxtGlobalShortcut failed to register: "Media Previous"
QxtGlobalShortcut failed to register: "Media Stop"
Application asked to unregister timer 0x1d00000a which is not
registered in this thread. Fix application.

The shortcuts do not work until I go into Preferences-> Global
shortcuts and make some changes. I must do this every time clementine
is started. Has someone found a solution? Aside from this, clementine works very well for
me, and I like it much better than amarok, which I always found
somewhat buggy.

---

### Post by TedN on 2011-09-22
> **fizikz said:**
> When I start clementine, I always get the following error messages in
the terminal:

virtual bool QxtGlobalShortcutBackend::DoRegister()
QxtGlobalShortcut failed to register: "Media Next"
QxtGlobalShortcut failed to register: "Media Play"
QxtGlobalShortcut failed to register: "Media Previous"
QxtGlobalShortcut failed to register: "Media Stop"
Application asked to unregister timer 0x1d00000a which is not
registered in this thread. Fix application.

The shortcuts do not work until I go into Preferences-> Global
shortcuts and make some changes. I must do this every time clementine
is started. Has someone found a solution? Aside from this, clementine works very well for
me, and I like it much better than amarok, which I always found
somewhat buggy.
_______________________________________

I have a similar problem.  {new installation of Ub 11.04}  Clementine actually worked when I installed it from the software center, but the next day it wouldn't launch at all.  Uninstalling and reinstalling doesn't help.  Uninstalling Banshee doesn't help.  The Clementine site:
[http://code.google.com/p/clementine-player/issues/detail?id=1976](http://code.google.com/p/clementine-player/issues/detail?id=1976)
says this is a known problem with Ubuntu, but implies it is related to Unity.  I am using Classic, and still have the problem.  I only had one evening with Clementine, and I fell in love and now it's gone!  Can anyone help.

---

