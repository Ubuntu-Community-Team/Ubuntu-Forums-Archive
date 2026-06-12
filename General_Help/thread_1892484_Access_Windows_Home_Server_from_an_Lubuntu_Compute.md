---
title: "Access Windows Home Server from an Lubuntu Computer"
date: 2011-12-08
forum: General Help
---

### Post by smartcard on 2011-12-08
I would like to know how to Access Windows Home Server from an lubuntu Computer on the Network similar to this : [http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/](http://www.howtogeek.com/howto/19389/access-windows-home-server-from-an-ubuntu-computer-on-your-network/)

---

### Post by Morbius1 on 2011-12-08
File Manager ( PCManFM ) > Go > Network Drives

---

### Post by smartcard on 2011-12-10
> **Morbius1 said:**
> File Manager ( PCManFM ) > Go > Network Drives

This works fine.

I need to know if there is way for the same function in Xubuntu?

---

### Post by Morbius1 on 2011-12-10
There is but you need to install a package that seems to have been not installed by default:
```
sudo apt-get install gvfs-backends
```After it's installed logout and login again and bring up thunar. In the left side panel should be an item labeled "Newtork" .

---

### Post by smartcard on 2011-12-10
> **Morbius1 said:**
> There is but you need to install a package that seems to have been not installed by default:
```
sudo apt-get install gvfs-backends
```After it's installed logout and login again and bring up thunar. In the left side panel should be an item labeled "Newtork" .

Cool, thank you it is working.:)

---

