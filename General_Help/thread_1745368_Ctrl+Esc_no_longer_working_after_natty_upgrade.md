---
title: "Ctrl+Esc no longer working after natty upgrade"
date: 2011-05-01
forum: General Help
---

### Post by TrevorBradley on 2011-05-01
Long story short, my HTPC has a keyboard, but no mouse.  I'd gotten pretty good at working the machine with no mouse, but after my upgrade to Natty Narwhal today, the Ctrl+Esc shortcut to open the Applications window no longer works.  Alt+F2 only works when another application is already open.   I can get to the Applications menu using Ctrl+Alt+NumLock and mouse emulation, but it's pretty painful.

Have I messed something up here?  My install went a little messy, but I've managed to get everything else working and I doubt a keyboard control would be a bad install/upgrade.

Any help would be appreciated!

---

### Post by BillDozer on 2011-05-04
I have the same problem. Someone found a solution?

---

### Post by brjhaverkamp on 2011-06-25
Goto:

Settings &#8594; Keyboard &#8594; Application Shortcuts &#8594;

Double click on  xfce4-popup-menu (default is Ctrl-Escape)

then select xfce4-popup-applicationsmenu.

It seems this "xfce4-popup-menu" is renamed to "xfce4-popup-applicationmenu"

Regards
RK

---

### Post by vanzandtj on 2012-10-21
> **brjhaverkamp said:**
> Goto:

Settings &#8594; Keyboard &#8594; Application Shortcuts &#8594;

Double click on  xfce4-popup-menu (default is Ctrl-Escape)

then select xfce4-popup-applicationsmenu.

It seems this "xfce4-popup-menu" is renamed to "xfce4-popup-applicationmenu"

Regards
RK

1) The application is "xfce4-popup-applicationsmenu" (with an "s"), because the menu label is "Applications" (with an "s").  You can confirm this with " ls /usr/bin/xfce4* "
2) On my system the shortcut was already listed as <Control>Escape, but that key combination didn't actually work. I used the "+" button to add a new shortcut with that key combination, and now it works.  The entry in the list is <Primary>Escape.  So they renamed both the application and the Control key!

---

