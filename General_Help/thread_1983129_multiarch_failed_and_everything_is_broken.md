---
title: "multiarch failed and everything is broken"
date: 2012-05-19
forum: General Help
---

### Post by dayzman on 2012-05-19
Hi

I tried to enable multiarch with:

```
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarchsudo 
apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386
```

it removed kile, okular, and many other packages. But now I can't install them again. If I try

```
sudo apt-get install kile
```

I get

```
The following packages have unmet dependencies.
 kile : Depends: konsole but it is not going to be installed
        Depends: kde-runtime but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any help will be appreciated.

Thanks

---

