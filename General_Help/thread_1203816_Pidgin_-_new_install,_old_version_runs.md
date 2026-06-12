---
title: "Pidgin - new install, old version runs"
date: 2009-07-03
forum: General Help
---

### Post by urusaiyatsu on 2009-07-03
I've updated pidgin numerous times from getdeb and now the ppa from the Pidgin site via the update manager. Everything seems to install without a problem.

But when I run pidgin via the Apps > Internet menu or ALT+F2 pidgin version 2.3.1 runs.

I'm stumped. What's going on here?

---

### Post by snakeman21 on 2009-07-03
running the commands on the Pidgin website only downnoads the upgrade packages.  It does not install them.  Go to System > Administration > Synaptic Package Manager and type "Pidgin" into the search box.  You should notice that the check box for Pidgin has a small star on it.  Click on it and select "Mark for Upgrade" and click apply.  Next time you start Pidgin, it will be the new upgraded version.

---

### Post by urusaiyatsu on 2009-07-03
Thanks for the info. But downloading the .deb files and using the package installer will install the latest version, right?

I have also removed pidgin, per the Getdeb instructions, and pidgin still runs 2.3.1. Could it be installed somewhere else and the links are pointing to the old install?

---

### Post by aesis05401 on 2009-07-04
> **urusaiyatsu said:**
> Thanks for the info. But downloading the .deb files and using the package installer will install the latest version, right?

I have also removed pidgin, per the Getdeb instructions, and pidgin still runs 2.3.1. Could it be installed somewhere else and the links are pointing to the old install?

If you are launching from the gnome menu system then you can view the launcher information by going to System/Preferences/Main Menu.

It is pretty intuitive from there.  If you want to see all the locations of the pidgin packages on your system you can open a terminal and type : sudo find / -name "pidgin"

You can then use the menu manager to add a new menu item pointed to the updated executable and remove the old one.

Edit: deb files are compatible with, but not necessarily configured for Ubuntu - thus the manual updating of the menu system.

---

