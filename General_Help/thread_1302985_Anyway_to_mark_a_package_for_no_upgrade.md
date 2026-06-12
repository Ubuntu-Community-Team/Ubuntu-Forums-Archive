---
title: "Anyway to mark a package for no upgrade?"
date: 2009-10-27
forum: General Help
---

### Post by Primefalcon on 2009-10-27
Is there a way to mark an an installed package to not upgrade or such in future apt-get upgrades?, and not even to ask if I want to upgrade that?

nvm I found the lock version in synaptic

for future reference in synaptic find the package you want to lock.., then go to the package menu and tick lock version

for for full apt functionality apt-pinning [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by dcstar on 2009-10-27
> **Primefalcon said:**
> Is there a way to mark an an installed package to not upgrade or such in future apt-get upgrades?, and not even to ask if I want to upgrade that?

nvm I found the lock version in synaptic

for future reference in synaptic find the package you want to lock.., then go to the package menu and tick lock version

for for full apt functionality apt-pinning [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Please read my sig if this is Solved.

---

### Post by pabloab777 on 2011-08-05
Try: **echo {PACKAGENAME} hold | dpkg --set-selections**

You can also (from man dpkg):
PACKAGE SELECTION STATES
[LIST=1]
[*]install   The package is selected for installation.
[*]hold   A package marked to be on hold is not handled by dpkg, unless forced to do that with option --force-hold.
[*]deinstall   The package is selected for deinstallation (i.e. we want to remove all files, except configuration files).
[*]purge   The package is selected to be purged (i.e. we want to remove everything, even configuration files).
[/LIST]
Or even easier: **aptitude hold/unhold {PACKAGENAME}**

---

