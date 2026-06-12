---
title: "Cannot Use Touchpad after Most Recent Ubuntu Update"
date: 2011-03-03
forum: General Help
---

### Post by alexp91k on 2011-03-03
*The problem:*
When I start the X server, my touchpad works for about 5-6 seconds (I'm moving it around to test). After the X server fully loads (and all the software loads in, I presume), the touchpad mouse promptly stops working. I can no longer use the GUI because the mouse is dead.

This seems to be a software bug after the latest update. Is there any way I can regress to a previous version? Perhaps uninstall the recently updated software?

---

### Post by vivek.pandey on 2011-03-03
i may not help if the problem is because of the server but here is a command which you should try after touchpad has stopped working
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

---

### Post by alexp91k on 2011-03-03
Wow, I am actually so grateful. Thank you so much; that worked like a charm. Awesome, thanks again.

---

