---
title: "OOo menu items remain after LibreO install from PPA"
date: 2011-02-08
forum: General Help
---

### Post by cscj01 on 2011-02-08
I installed Libreoffice from the PPA and understood OOo would be removed.  However Openoffice.org Drawing and Openoffice.org Formula remain in the Office Menu.  I ran
```
sudo apt-get purge openoffice*
```

but this removed my libreoffice-report-builder plugin and not the menu items.  What should I check to see if any of OOo is still around, and how do I get rid of it without removing something Libreoffice uses?

---

### Post by fragos on 2011-02-08
Right click the Ubuntu icon, upper left, and select Edit Menus. That will give you access to edit the menus or just hide menu items by un-checking.

---

### Post by cscj01 on 2011-02-09
> Right click the Ubuntu icon, upper left, and select Edit Menus. That will give you access to edit the menus or just hide menu items by un-checking. 
I understand how to inactivate the items that appear on the menu.  What I really am asking is why they are still there if they were removed (the apps themselves), and if they were not removed, why not?  Are there pieces of code, config files, and directories that remain from OOo?  If so, where are they?

After this post, I discovered the following issue: [http://ubuntuforums.org/showthread.php?t=1684025]("http://ubuntuforums.org/showthread.php?t=1684025")

This leads me to believe that the packaging of Libreoffice in the PPA depends on some components from the OOo install.  If that is so, it may explain why my toolbars would not work properly after I purged the OOo items using Ubuntu Tweak.

---

### Post by fragos on 2011-02-09
I uninstall-ed all OO components before installing LibreOffice and had no problems. Since one is a fork of the other clearly there are common dependencies.

---

### Post by cscj01 on 2011-02-11
I may as well mark this as solved.  The answer is probably contained in the approach to removing OOo and installing LO.

---

