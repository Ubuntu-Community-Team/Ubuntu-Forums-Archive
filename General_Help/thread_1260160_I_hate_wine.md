---
title: "I hate wine"
date: 2009-09-07
forum: General Help
---

### Post by joshjh on 2009-09-07
I downloaded wine to try out itunes on ubuntu, but of course it caused more problems. First when i had wine installed it wouldnt uninstall itunes or quicktime, just reinstall them. Now i uninstalled wine and it is still in my applications tab with itunes and quicktime. Any idea how to get rid of these? According to KlamAV i had viruses in wine too. Great, Windows ruins my life even when im not really using it. Any help would be very much appreciated. Thanks

---

### Post by P4man on 2009-09-07
Have a beer then :)

No need to hate wine, hate Apple for not making a linux version.
iTunes doesnt work under wine, save yourself the trouble. If you must use it, install virtualbox and install windows in it.

As for the virus. I honestly dont know if a wine setup can get infected. I suspect it might (though it would be pretty harmless to the rest of the system I guess), but I wouldn't trust a virusscanner running under wine. Try a linux virus scanner instead. Or just remove the stuff from ~/.wine/drive_c

edit: you're already using clamav.. missed that. Anyway, if you downloaded the stuff from apple, I wouldn't worry too much. Probably false alarm

---

### Post by 3rdalbum on 2009-09-07
> **joshjh said:**
> I downloaded wine to try out itunes on ubuntu, but of course it caused more problems. First when i had wine installed it wouldnt uninstall itunes or quicktime, just reinstall them. Now i uninstalled wine and it is still in my applications tab with itunes and quicktime. Any idea how to get rid of these? According to KlamAV i had viruses in wine too. Great, Windows ruins my life even when im not really using it. Any help would be very much appreciated. Thanks

Remove them with the menu editor - Right-click Applications and go to Edit Menus. Uncheck the Wine submenu.

I think I've seen false alarms in my .wine directory too in the past - certain Javascripts that ship with Dreamweaver were marked as "nuisances" or something in ClamAV.

---

### Post by nbtrap on 2009-09-07
^^^Don't do that

To remove the menu entries the proper way, first of all, recheck them in the menu editor if you listened to this guy's advice. Then, delete the "applications-merged" folder from /home/<name>/.config/menus

To remove wine mime-types, delete the folder /home/<name>/.local/share

Then run:

```

sudo killall gnome-panel

```

There you go.

---

### Post by XCan on 2009-09-07
Hehe, in general one should always check the appdb [http://appdb.winehq.org/](http://appdb.winehq.org/) befeore attempting to run a major Windows app. :)

---

