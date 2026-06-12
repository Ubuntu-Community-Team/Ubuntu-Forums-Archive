---
title: "Touch Screen Support"
date: 2011-12-28
forum: General Help
---

### Post by tsx_5 on 2011-12-28
Hi,

I have a Candor multi touch touchscreen.  X recognizes it fine and it is listed as "Multi touch panel with controller" in xorg.log.0.  When I press the screen the cursor follows the touches as expected, however, touches result in more than one event (ie: multiple mouse button presses).  Additionally, xorg.log.0 shows an error message "evdev-grail failed to open grail, no gester support".  

This is all under Ubuntu 11.10 (fully updated).  

How do I troubleshoot/fix this?  Thanks in advance,

tsx_5


BTW: X is assigning this as a type (tablet)

---

### Post by pretty_whistle on 2011-12-28
"... touches result in more than one event (ie: multiple mouse button presses)."?  It sounds like it's set to sensitive.

---

### Post by tsx_5 on 2011-12-29
Turns out I didn't have the xorg multitouch server installed.  Once it was installed button presses worked as expected, however, kinetic scrolling didn't.  Will have to keep looking at that.

---

