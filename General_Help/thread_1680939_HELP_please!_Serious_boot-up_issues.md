---
title: "HELP please! Serious boot-up issues"
date: 2011-02-03
forum: General Help
---

### Post by LanguidLegend on 2011-02-03
OK, so I just did
```
sudo apt-get remove Python
```
because I wanted to remove 2.6 and install/upgrade to 3.1,
and in the middle of the long removal process, the screen went black and I was forced to force-reboot the computer.
However, there were startup errors and it can only start in low-graphics mode now (i.e.:command-line only). :\

Is there any way to restore the system?

---

### Post by oldfred on 2011-02-03
You used to not be able to get to command line, so they have changed something. And then only a chroot into system would let you fix it.

Ubuntu runs on python 2.6 you cannot uninstall it. You just also install other versions of python and then in each program specify which version to use. Default has to remain 2.6.

Reinstall python.

sudo apt-get install python

If it also uninstalled lots of other programs you may need to reinstall the desktop.

# reinstall desktop
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

---

### Post by LanguidLegend on 2011-02-03
> **oldfred said:**
> Reinstall python.

sudo apt-get install python

If it also uninstalled lots of other programs you may need to reinstall the desktop.

# reinstall desktop
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

Installed python then uninstalled/reinstalled the desktop, no change. :\

---

### Post by oldfred on 2011-02-03
Reupdate everything:

if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install

You probably also have to reinstall video driver to get good graphics. Did you originally install a nVidia or other proprietary driver?

Not sure what other packages depend on python and also were uninstalled.

---

