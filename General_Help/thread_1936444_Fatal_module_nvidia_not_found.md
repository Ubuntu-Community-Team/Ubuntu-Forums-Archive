---
title: "Fatal: module nvidia not found"
date: 2012-03-06
forum: General Help
---

### Post by asuastrophysics on 2012-03-06
Hey guys,

I recently upgraded from 11.04 to 11.10, and I can't for the life of me figure out why I can't get get X to start properly. I tried chrooting into the partition and running the following:
```
sudo apt-get remove purge nvidia*
```
Followed by:
```
 sudo apt-get install linux-headers`uname-r'
sudo apt-get install nvidia-current
```
It installs correctly, but makes zero difference. I still get the same error. I even installed an old kernel and tried to boot that, but that doesn't seem to work either.

How to I make my computer work again? What driver is necessary to make an nVidia GeForce 8600GT function properly? Thanks a ton in advance!

---

