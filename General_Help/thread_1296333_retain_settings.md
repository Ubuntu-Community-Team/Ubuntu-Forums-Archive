---
title: "retain settings"
date: 2009-10-20
forum: General Help
---

### Post by oohbuntoo on 2009-10-20
Is it possible to save settings before upgrading and/or changing distros?  Example:  If I want to play with Karmic 9.10 is there a way to save my present settings from Jaunty and install them in Karmic so I don't have to go through the motions of installing everything again?

---

### Post by undecim on 2009-10-20
Your home folder keeps all your user settings. Copy it over, and you will keep those.

To get a list of all packages you have installed, run this in a terminal:
```
dpkg --get-selections > installed-software
```To put those packages back in your new ubuntu install:
```
dpkg --set-selections < installed-software
dselect
```Though some packages may have changed or been removed from the new Ubuntu version, so you might want to just install the ones you use manually.

EDIT: Also, system-wide settings are stored in /etc/, so copy any settings you need from there.

---

### Post by Giblet5 on 2009-10-20
Yeah. It's called VirtualBox or VMware. ;)

Wait for the release, then do an upgrade. What could be easier?

---

### Post by P4man on 2009-10-20
basically: no
Having a separate /home partition, making a backup of your apt cache and list your installed packages goes a long way, but its not a single click "revert upgrade". Far from.

Best bet is trying karmic on a separate partition.

---

