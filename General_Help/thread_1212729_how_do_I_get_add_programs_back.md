---
title: "how do I get add programs back?"
date: 2009-07-14
forum: General Help
---

### Post by Arminius on 2009-07-14
just reinstalled mythbuntu 9.04, and now the add programs is missing?
can't think it was either under settings or system.

anyway, how do I bring it back?

---

### Post by earthpigg on 2009-07-14
if you mean synaptic package manager, its in system -> administration.

if it isn't there, you can probably install it via command line:

> sudo apt-get install synaptic

---

### Post by Arminius on 2009-07-14
O it's not synaptic, the other one, which ever colum it's in it was always at the top in mine, and think it was titled add/remove applications

---

### Post by Arminius on 2009-07-14
bump

---

### Post by Marlonsm on 2009-07-14
-Go to: System > Preferences > Main Menu
-On the left part of the window, select the applications menu.
-Click "New Item" and put (only the "Type" and "Command" ones are needed, you can put whatever you want in the others):
Type: Application
Name: Add/Remove...
Command: /usr/bin/gnome-app-install
Comment: Install and remove applications
-Click OK and it's done.
-If you want to make it look just like the one that comes with Ubuntu, add a separator before it.

---

### Post by mikewhatever on 2009-07-14
If you reinstalled from the regular desktop cd, the Add/Remove entry should be the last one under Applications. Verify the package is installed with **dpkg -s gnome-app-install** command from Terminal.
It is, most probably, a menu refresh issue of some kind. Right click on the menu, select 'Edit Menu', click on Applications in the left panel and look for add/remove in the right one, it should be the last one. Make sure the box next to it is ticked, if it is, then un-tick it, and then re-tick again.

---

### Post by Arminius on 2009-07-14
ok Marlonsm, there is no Preferences under system
and mikewhatever, there is Edit Menu when I right click on applications.

I put what u wanted in terminal, it just game up with "Package `gnome-app-install' is not installed and no info is available."

---

### Post by earthpigg on 2009-07-14
> **Arminius said:**
> 
I put what u wanted in terminal, it just game up with "Package `gnome-app-install' is not installed and no info is available."

```
sudo apt-get install gnome-app-install
```

---

### Post by Arminius on 2009-07-14
thank you, that worked perfectly

---

