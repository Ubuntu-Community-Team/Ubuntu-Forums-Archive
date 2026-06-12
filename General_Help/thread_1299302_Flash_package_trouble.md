---
title: "Flash package trouble"
date: 2009-10-23
forum: General Help
---

### Post by charrah on 2009-10-23
I'm using the Ubuntu Karmic beta (I suppose the packages have upgraded to the RC's now) and the package adobe-flashplugin wants to upgrade, but fails giving an error that a script exited with a failure. Attempting to remove it gave an error that it is seriously broken, so it needs to be reinstalled. But of course, the package only has the new version available.

How do I manually remove this package?

---

### Post by Brandon Williams on 2009-10-23
You can edit /var/lib/dpkg/info/adobe-flashplugin.prerm. You need to use sudo to do this. There is a line that says 'set -e'. Change it to '#set -e'.

With this change, you will be able to uninstall adobe-flashplugin.

---

### Post by charrah on 2009-10-23
I made the change but apt-get and synaptic are bent on reinstalling it; when I start either, they say
```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```
When I try to uninstall it through aptitude it says that problems occurred with that package and it couldn't finish.

---

### Post by charrah on 2009-10-24
Managed to remove the package by looking at dpkg's man page. Used command
```
sudo dpkg -P --force-remove-reinstreq adobe-flashplugin
```

---

