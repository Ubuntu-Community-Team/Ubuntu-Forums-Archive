---
title: "gnome-panel freezes in Ubuntu 9.10 64bit"
date: 2010-01-22
forum: General Help
---

### Post by nadeem.ansari on 2010-01-22
My gnome-panel freezes frequently.

Temporary solution: I have added gnome-terminal to my startup programs, and enter "killall gnome-panel" command whenever the panel freezes. However, this is inconvenient especially when the panel freezes every now and then.

Quite interestingly, all icons, menus, and applets freeze including run dialog [Alt-F2], except logout, battery, volume, etc. in the system (applets indicator) tray [time & calendar icon also freezes in system-tray].

additional thoughts:
In an old post, someone suggested a problem with evolution calendar. I have tried killing all processes related to evolution, but to no avail. someone also suggested removing applets... well, it is not mentioned which applet to remove..

waiting for suggestions and help.
Thanks.

---

### Post by nadeem.ansari on 2010-01-22
I think my problem is related to the following bug(s). However, this might be only one of the problems causing the panel to freeze. I had the gnome-panel on left or right and width set to more than 30. Opening more than 7 windows freezes it.

I have moved the panel back to top (although I prefer to save vertical space) and will observe if the panel freezes (due to other unknown reasons) in that location or not.

gnome-panel freezes:
  bug: [https://bugzilla.gnome.org/show_bug.cgi?id=513347](https://bugzilla.gnome.org/show_bug.cgi?id=513347)
  bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/187540)

---

### Post by simonrodan on 2010-03-30
I have experienced the same issue where the panels are on either side rather than top and bottom and set to 32 pixels wide. The problem appears in both 32 and 64 bit versions.

---

### Post by friend4u on 2011-03-17
Hi,
  Did this issue got fixed? I have problem with freezing panel. I moved my panel to bottom. Whenever system started time don't display and wireless icon don't visible. System runs fine through. If I select panel position to top and then select bottom again all works fine. Any solution to this?
Thanks and regards

---

