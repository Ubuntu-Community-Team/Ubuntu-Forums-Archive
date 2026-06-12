---
title: "Wine"
date: 2009-11-17
forum: General Help
---

### Post by Cityscape on 2009-11-17
Where can I get the latest .deb package for WINE? I've looked but cannot seem to find it.

---

### Post by ColdLunch on 2009-11-17
Are you looking specifcally for the .deb or are you trying to install it?

---

### Post by fluffman86 on 2009-11-17
You can use a stable version of wine with simply:
sudo apt-get install wine

Or you can use a more up-to-date version of wine by going to System > Administration > Software Sources, then click the "Other Software" tab, then Add... and paste this into the box:
ppa:ubuntu-wine/ppa

And reload your sources.  Now, if you already have wine installed, it will update the next time you run update-manager, or you can install wine with the command above and the testing version will supersede the old version.

---

### Post by berman56 on 2009-11-17
Is this what you are looking for:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

