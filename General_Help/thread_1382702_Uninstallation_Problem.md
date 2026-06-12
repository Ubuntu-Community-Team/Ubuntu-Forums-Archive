---
title: "Uninstallation Problem"
date: 2010-01-16
forum: General Help
---

### Post by Dark Sorrow on 2010-01-16
I installed a lot of crap in my system and after it got full i started to uninstall it using
```
 sudo apt-get autoremove *(software name)
``` command in the terminal and through Add-Remove Program dialog box. The software were successfully removed i.e. the memory space was released but the name to software still remains in the Application --> *(sub tabs like education, office, programming, etc.) tabs respectively. Please guide me how remove the names of softwares from their respective tabs. This problem also pretains in case of wine, even if i have unistalled an software it name still remain in Wine --> Program tab.
Also guide if their is a way to install software in other place than /usr/bin folder like some other media(just like we can install softwares in C: or D: drives in Windows).

---

### Post by nullmind on 2010-01-16
Wine notices when .lnk files are written and makes launchers out of them, and puts them into the Wine menu, but right now it doesn't take them out when deleted. It probably won't anytime soon, and I don't request the feature myself since I don't want it deleting anything.

Changing /usr/bin is a bad idea, try working with $PATH instead. Unless you have a compelling reason.

---

### Post by oldos2er on 2010-01-16
**sudo apt-get autoremove** uninstalls unneeded dependencies of packages no longer installed. Did you mean **sudo apt-get remove**? If so, it should delete menu entries. You can also try **sudo apt-get purge**.

It's also possible to manually edit your Applications menu by right-clicking on it and choosing 'Edit Menus'.

---

