---
title: "enabling wireless"
date: 2010-05-20
forum: General Help
---

### Post by thedork01 on 2010-05-20
I recently installed ubuntu 10.04 to dual boot with windows 7.  When I boot ubuntu from the live cd wireless works fine, but when I try to connect from the installed version Wireless is disabled and will not allow me to enable it.

ifconfig reveals that wlan0 is up but not connected.

Anyone have any suggestions?

---

### Post by silkworm2.5 on 2010-05-20
Try right clicking on the network icon and click "enable wireless" If that fails, go into System > Administration > Users and groups
From there: Advanced settings > User privileges. Tick all the boxes, then try enabling it again.

---

### Post by Peter09 on 2010-05-20
Have you used the update manger since installation - some wireless drivers will be downloaded when you collect the updated packages. Connect to a wired connection and do

System->Admin->Update Manager

---

