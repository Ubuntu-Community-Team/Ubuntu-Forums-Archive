---
title: "PLEASE Help! Update problem!!!!"
date: 2011-05-09
forum: General Help
---

### Post by Fungle10 on 2011-05-09
Ive asked this question before nobody replied but PLEASE help me!

After going back today I went on the software centre and it doesn't work AGAIN! I don't know why, When I was at college there was a message about a .Local domain and a network discovery thing but that's all I know.

PLEASE help me

-------------------

[http://ubuntuforums.org/showthread.php?t=1744536](http://ubuntuforums.org/showthread.php?t=1744536)
Fixed it with this guide, Someone give that guy a medal!

---

### Post by dino99 on 2011-05-09
use synaptic instead of software-center and watch logs: xsession-errors & /var/log to know about errors

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

