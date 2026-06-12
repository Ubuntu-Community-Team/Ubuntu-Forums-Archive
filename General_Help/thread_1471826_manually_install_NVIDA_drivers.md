---
title: "manually install NVIDA drivers"
date: 2010-05-03
forum: General Help
---

### Post by acejoneyboy on 2010-05-03
how can i manually install NVIDIA drivers for kubuntu? my computer that has the kubuntu OS is not connected to the web.

---

### Post by micheledm on 2010-05-03
Download the .run package from nVidia website, then stop GDM from console
```
sudo services gdm stop
```
now from the console navigate to the .run package, make sure that it is executable and run it, then go through the installation process.

---

### Post by tekkidd on 2010-05-03
1) Download drivers from nVidia site
2) CTRL+ATL+F1
3) sudo /etc/init.d/kdm stop
4) cd /location/of/file
5) chmod +x filename
6) ./filename
7) Follow installer 
8) sudo /etc/init.d/kdm start

---

### Post by acejoneyboy on 2010-05-03
thanks, one more thing, is there a website that i can just download programs for kubuntu?

---

### Post by acejoneyboy on 2010-05-04
its saying that the command is unknown

and i tried it on ubuntu and it just opens terminal up and stops the install

---

