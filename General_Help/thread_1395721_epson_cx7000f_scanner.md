---
title: "epson cx7000f scanner"
date: 2010-02-01
forum: General Help
---

### Post by ksonken on 2010-02-01
download to get scanner to work .printer is fine as is copier think i need E_DUP10.EXE to download but really dont know can someone send me a link

---

### Post by Psumi on 2010-02-01
Drivers from windows for anything but network cannot be installed on linux. Just so you're also aware, WINE's goal is NOT to have hardware compatibility, so DO NOT install drivers with it.

Try installing libsane-extras from terminal (applications > accessories):

```
gksudo apt-get install libsane-extras
```

For those who want to give support to this user: Make sure you explain to the user the caveat of plain sudo (the "password-doesn't-show-as-you-type" issue that most GUI users get nuts about.)

---

### Post by ellgor on 2010-02-01
Hi,

If your still stuck, go to the "Avasys" site, its for Epsons, and get their ImageScan package, works after a reboot.

Regards, Ellgor.

---

