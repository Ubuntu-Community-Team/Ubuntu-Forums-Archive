---
title: "Add New Items to xfce4-panel no longer working"
date: 2012-01-04
forum: General Help
---

### Post by MartijnNL on 2012-01-04
Hello,
On a machine I've been running Xubuntu 10.10 for some time now. I had replaced xfce4-panel with the Avant Window Navigator (AWN). However I'm considering switching back to the xfce4-panel (referred to as panel from here on) to improve startup speed (specifically the time after login).

I started xfce4-panel, killed AWN, added a few items like a notification area (systray). I found that the quit button in the panel just quit the panel and not the system. So I started AWN again, rebooted using it's quit button (saving session state). After logging in I got a warning of a notification area already being present (because there was one in the panel and one in AWN). Ignored that, killed AWN and rebooted again (using the now working quit button on the panel) to save the new session state with panel and without AWN. When I logged in again, I had no notification area on the panel.

Since then I'm completely unable to add any items to the panel. No systray, no launchers nothing. The Add New Items window works, but when I drag anything to the panel, nothing happens.

Any ideas to why this may happen?

Martijn

---

### Post by mike555 on 2012-01-04
I believe you need to add a "launcher" to the panel first then drag something into it .

---

### Post by MartijnNL on 2012-01-04
Problem solved. I had removed an auto-expanding separator. This seems to have prevented me from moving applets an thus also from dragging something from the window to the panel. I noticed first that the Add button in the Add New Items window worked. But I couldn't move anything. Some more googling into that suggested the expanding separator. And now things are working again.

Marked as solved.

---

