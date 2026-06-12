---
title: "If I copy all files from system files onto a usb hdd will It backup all programs?"
date: 2009-09-17
forum: General Help
---

### Post by rock it on 2009-09-17
Hi,
If I copy all system files onto a portable hdd will I be able to re-install xubuntu then copy all system files back on and use the programs I previously had installed.

Thanks,

sorry if its a stupid question.

---

### Post by jondkent on 2009-09-17
Hi,

By system files do you mean /etc?  Or other dirs?

---

### Post by StuartN on 2009-09-17
> **rock it said:**
> If I copy all system files onto a portable hdd
sorry if its a stupid question.

Probably no, because you need your user settings too (these are usually held in directories like ~/.gimp-2.6) and because there may be version dependencies and links between applications and the system.

---

### Post by wojox on 2009-09-17
Try:

```
sudo dpkg --get-selections > myPackages
```

Creates a list of all packages currently installed. Save that file to somewhere safe.

Reinstall:

```
sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

This takes the packages from list and installs just like it was before re-install.

---

### Post by dmizer on 2009-09-17
> **wojox said:**
> Try:

```
sudo dpkg --get-selections > myPackages
```

Creates a list of all packages currently installed. Save that file to somewhere safe.

Reinstall:

```
sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

This takes the packages from list and installs just like it was before re-install.

In addition to that, make a backup copy of your /home/$you directory, and you should be right back where you started (with the exception of hand configured /etc/$program.conf files)

---

