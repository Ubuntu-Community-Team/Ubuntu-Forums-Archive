---
title: "lost the little wireless icon from the taskbar?"
date: 2009-08-31
forum: General Help
---

### Post by georgeeboy on 2009-08-31
***hey everyone, i am connected to the correct wireless network and internet is working fine....although i seem to have either deleted the wireless icon from the taskbar or it disappeared by itself.  It's not on "add new panel" can anyone help? ***

---

### Post by oboedad55 on 2009-09-01
> **georgeeboy said:**
> ***hey everyone, i am connected to the correct wireless network and internet is working fine....although i seem to have either deleted the wireless icon from the taskbar or it disappeared by itself.  It's not on "add new panel" can anyone help? ***

No guarantee that this will solve your problem but it will restore the menu bars to the default that you first had installed. Bear in mind that you'll lose any customization you have, but you can fix that back up.

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart
I have one other thought. You can try reinstalling network-manager-gnome and see if that will restore the icon.

--Jon

---

### Post by Vishnu V on 2009-09-01
Add 'notification area' from add to panel

---

