---
title: "Install package issues"
date: 2011-04-22
forum: General Help
---

### Post by marley1 on 2011-04-22
Hi

Installed ubuntu 10.10 on my dell D600. Install went fine, but after updates, the initial startup sound disappeared.  Also had a bit of an issue getting the wireless card to work, eventually found the answer in the debian wiki and got the legacy installer for the b4X broadcomn chipset.  Since then, everytime i install something, the system tells me the package was not installed correctly, but it does appear to install, except the stellarium.  Anybody had these issues before??

Thanks

---

### Post by spikoley on 2011-04-22
Try the following commands.

```
sudo apt-get install -f
```
```
sudo apt-get update
```

---

