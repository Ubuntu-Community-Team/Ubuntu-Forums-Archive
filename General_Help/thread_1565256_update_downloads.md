---
title: "update downloads"
date: 2010-08-31
forum: General Help
---

### Post by Grey Seal on 2010-08-31
Dell GX, 10.04, FF 3.6.8; Suddenly unable to download Linux updates so first thought was to browser. Checked file mgr for an exe to reload yet could not locate. During the process was unable to open a few OS application files, unfortunately could not cut and paste explanations and too stupid to locate files in which they might be saved. 

Unfamiliar with this OS yet my first intuition is to remove the latest browser version 3.6.8.tar.bz2 and reinstall from URL. Even so, have never used OS uninstall and have no idea what might be lost in new bookmarks which do not transfer correctly to the other POP.

Any assistance appreciated,
GS

---

### Post by blazemore on 2010-08-31
Open a terminal (Konsole)

Type the following commands and press Enter after every one.
If it asks for your password, type your password in and press Enter. You won't see any visual feedback while doing so.

```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install --reinstall kubuntu-desktop
```

---

### Post by Grey Seal on 2010-08-31
Thanks, interesting. Very similar to the DOS days. 

It rewrote but still not downloading the updates. Maybe it is in the browser.

Appreciate the time,

GS

---

