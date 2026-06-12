---
title: "nm-applet,volume control and battery icon missing"
date: 2009-11-03
forum: General Help
---

### Post by b-boy on 2009-11-03
Hi all
I have just installed 9.10 and since the installed the following icons are missing in the system tray

**nm-applet,volume control and battery icon**

I can start nm-applet manually but I would like for it to start up automatically

---

### Post by pastalavista on 2009-11-03
Right-click on the panel where you want the "system tray" to be and select "Add to panel" from the menu. Then select "Notification Area" from the list and click "Add".

---

### Post by b-boy on 2009-11-03
> **pastalavista said:**
> Right-click on the panel where you want the "system tray" to be and select "Add to panel" from the menu. Then select "Notification Area" from the list and click "Add".

have tried that but it does not work either

---

### Post by pastalavista on 2009-11-03
> **b-boy said:**
> have tried that but it does not work either

I guess that means it's broken. Try booting in recovery mode and 'fix broken packages' and then go to root console with networking and run ```
sudo aptitude safe-upgrade
``` and then reboot normally.

---

### Post by uaneme on 2010-01-16
press alt-f2  nm-applet --sm-disable

---

### Post by Glesshoppa on 2010-03-21
Thank you!! _uaneme_ for this fix it worked wonderfully.  Does anyone know why the nm-applet disappears? All I did was delete an entry in my wireless properties and the applet vanished.

---

