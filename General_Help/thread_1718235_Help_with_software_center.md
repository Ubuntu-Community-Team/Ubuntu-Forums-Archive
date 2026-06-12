---
title: "Help with software center"
date: 2011-03-31
forum: General Help
---

### Post by zenawenliang on 2011-03-31
Ok so I downloaded SuperTux 2, and Once I dwonloaded it it was applying changes and then this happens,

Errors were encountered while processing:
 firmware-b43-lpphy-installer
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:1713
14e4:4328)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

This HAS BEEN HAPPENING EVERYTIME, I go through applying changes, please help!!:confused:

---

### Post by zenawenliang on 2011-03-31
bump

---

### Post by falko on 2011-03-31
Have you tried to uninstall that package?
```
apt-get purge firmware-b43-lpphy-installer
```

---

