---
title: "HPLIP Status-"
date: 2011-05-07
forum: General Help
---

### Post by Densdoor on 2011-05-07
Alert says No System Tray detected on this system, unable to print - exiting

Well man oh man I docked that thing to the taskbar, I undocked it. I said NO Notices of any kind (not exact words for) But everytime I reboot up Ubuntu about 1-2 minutes or so in, there comes that alert.

-Dennis

HPLIP is for Printer BTW for those who might not know.

---

### Post by maarten256 on 2011-05-22
I ran into the same problem after I toyed around with my panels (and managed to delete the whole nine yards, including the bar itself).

Took me a little while to get it back to the way it was. The hplip status icon took me the longest to figure out.

While the error says it can't find a system tray, in reality it's looking for a notification area... So right click on the panel, select "Add to panel" and then select "Notification Area". This will add a blank "area" to the Panel (indicated only by the divider).

After this, you can run hp-systray from an xterm and it should pop the icon in place... After that you shouldn't have that bothersome error message anymore either. If, when you run hp-systray from the xterm you get an error like "is hp-systray already running?" (or words of that nature), run "ps -ef | grep systray" and use kill to kill all running instances of hp-systray.

Hope this works for you as it did for me!

BTW - I'm running Ubuntu 11.04, pretty sure the instructions above are good on Ubuntu 10.10 as well. Can't say anything about other Linux distros.

---

