---
title: "Mouse Setting Not Retained"
date: 2010-06-24
forum: General Help
---

### Post by pricetech on 2010-06-24
Okay, let me start by saying I know this is an Ubuntu forum and my question is about windows, but I'm hoping I can find the brain power necessary to fix this here since it seems sadly lacking elsewhere.

Windows XP SP3 on a Dell Optiplex 755 less than a year old.  The user is left handed and therefore swaps the mouse buttons in Control Panel - Mouse.  For some reason that setting is not retained over a reboot.  I've loaded the registry hive for that user and checked the setting and it is correct before the user logs on but somehow gets reset at login.

Any ideas ???

Thanks in advance.

---

### Post by pricetech on 2010-06-29
Solved, though it doesn't make sense.  I disabled "HotKeyCommands" (hkcmd.exe) which is part of the Intel video driver and allows for adjustment of the display using hotkeys.  Not used at all here except by the occasional smart___ who thinks it's funny to turn the display upside down.

Note to self:  Add disabling this as a step in my standard setup.

---

