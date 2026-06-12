---
title: "Unable to download OpenOffice in Ubuntu 11.04"
date: 2011-08-19
forum: General Help
---

### Post by pb910 on 2011-08-19
i cant seem to download openoffice for ubuntu 11.04.

I have tried installing it from the software centre (i've tried reinstalling too), but the app finder can't find the openoffice suite, and when I locate the file through my home folder (/usr/share/app-install/desktop/ooo-meta.desktop), I try opening it, and the following error message appears: "Could not display "/usr/share/app-install/desktop/ooo-meta.desktop"

 can someone point me in the right direction please?

---

### Post by IWantFroyo on 2011-08-19
OpenOffice has been replaced with LibreOffice (same thing, with more open source-ness and better MSO integration).

If you really want OO:
```
sudo apt-get purge libreoffice
```

Then go to OpenOffice.org, download and install the .deb.

---

### Post by Machiavelli on 2011-08-19
You don't whant OpenOffice.

try LibreOffice.

---

