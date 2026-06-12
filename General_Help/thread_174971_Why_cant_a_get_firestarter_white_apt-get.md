---
title: "Why cant a get firestarter white apt-get"
date: 2006-05-12
forum: General Help
---

### Post by mattiashem on 2006-05-12
Wy cant a get firestarter whith apt-get.

Im using edubuntu 5 ant try with both

apt-get install firestarter
och sudo apt-get install firestarter 

i have updated apt-get both nothing is hapening.
Try to grab it with synapt to but nothing happens.

Any ide ??

---

### Post by aysiu on 2006-05-12
Try this: ```
cd /etc/apt
sudo mv sources.list sources_old.list
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv breezy.list sources.list
sudo apt-get update
sudo apt-get install firestarter
```

---

