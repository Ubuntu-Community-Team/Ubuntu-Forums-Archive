---
title: "Update Manager is not Working"
date: 2010-04-02
forum: General Help
---

### Post by UCSBGauchosRock on 2010-04-02
Okay so here is my situation... I cannot open update manager...

1.I tried opening from menu but that didn't work.
2.I tried Alt+F2 and typing update-manager but that didn't work.
3.Same as #2 but typed update-manager -d.

Information
Ubuntu 9.10 Karmic Koala 2.6.31-21 kernel

Thank You Very Much :)

EDIT: I'm sorry I forgot to mention. I want update-manager -d to be able to upgrade to Lucid Lynx when stable version comes out. I don't like updating via terminal.

---

### Post by Elfy on 2010-04-02
If you want to upgrade to lucid when it releases then in Software Sources - Update tab at the bottom - Release Upgrade - normal releases.

If you have an issue with update-manager try opening it from a normal terminal and seeing the errors in there.

---

### Post by TChiOBi on 2010-04-02
> **UCSBGauchosRock said:**
> Okay so here is my situation... I cannot open update manager...

1.I tried opening from menu but that didn't work.
2.I tried Alt+F2 and typing update-manager but that didn't work.
3.Same as #2 but typed update-manager -d.

Information
Ubuntu 9.10 Karmic Koala 2.6.31-21 kernel

Thank You Very Much :)

EDIT: I'm sorry I forgot to mention. I want update-manager -d to be able to upgrade to Lucid Lynx when stable version comes out. I don't like updating via terminal.
what worked for me was just opening a terminal inside gnome(no ALT+F2) and type:
update-manager -d
thou cause me more problems then ever upgrading so i ended up downloading the .iso file (wich you can burn to a cd or with UNetBootIN put in on an usb stick/flash drive ~ just make sure you format the stick first to FAT32 and it's flaged bootable) and clean install worked like a charm.

but, if you want to still upgrade to test you could also try this:
log out of gdm
switch to ALT+F1 or F2 and login
try these commands:
sudo service gdm stop
sudo apt-get update
sudo apt-get dist-upgrade

hope this helps

---

