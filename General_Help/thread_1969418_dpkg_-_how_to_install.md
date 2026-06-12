---
title: "dpkg - how to install"
date: 2012-04-30
forum: General Help
---

### Post by malakar.subhendu on 2012-04-30
to install a package by the dpkg command is:
```
sudo dpkg -i package_name.deb
```

this installs the package correctly.
but if there is a similar package with newer/stable version already installed in the machine, it replaces the newer version with the given version. i want to know if there is some method (-something) which will check the packages first for newer one and will install the file only if any new one is not available.

---

### Post by josephmills on 2012-04-30
```
dpkg-query -l 

```
or 
```
apt-cache policy dump <package>

```
or 
use *lintian* for package
or just use apt and a repo

---

