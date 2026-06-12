---
title: "Possible to upgrade from Ubuntu to xubuntu without clean install?"
date: 2011-09-12
forum: General Help
---

### Post by GammaPoint on 2011-09-12
In an attempt to avoid Unity/Gnome3 I would like to use xubuntu with the XFCE desktop environment. I'm currently running Ubuntu 10.10 and am wondering if I can somehow simply upgrade to Xubuntu without doing a clean install. Just looking for the easiest way to do it without messing with setting up partitions and all that.

---

### Post by saltmarshlamb on 2011-09-12
You could try installing xubuntu-desktop and removing the ubuntu files, then the upgrade should just upgrade xubuntu.

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
[http://www.psychocats.net/ubuntu/purexfcemaverick](http://www.psychocats.net/ubuntu/purexfcemaverick)

Personally I'd back up and install xubuntu over the existing install.

---

### Post by Synoc on 2011-09-13
ubuntu/kubuntu is not a matter of an upgrade, it's an interface and a skin. 


```
sudo apt-get  install kde-full 
``` will give you the KDE interface and allow you to keep Ubuntu's standard interface as well, you select which one will be your default, but you can switch to the other at the user sign-on the added HDD space for the KDE interface is minimal.

---

### Post by GammaPoint on 2011-09-13
I ended up going with a clean install. Thanks for the help everyone.

---

