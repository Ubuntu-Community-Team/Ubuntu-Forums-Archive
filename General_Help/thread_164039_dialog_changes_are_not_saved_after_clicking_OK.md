---
title: "dialog changes are not saved after clicking OK"
date: 2006-04-22
forum: General Help
---

### Post by sbddude on 2006-04-22
In the wireless network settings, I need to clear the key for WEP. If I erase the ******* where the key is, click OK, then go into settings again, the key is still there! Help!

---

### Post by Ramses de Norre on 2006-04-22
sudo gedit /etc/network/interfaces
Remove the line about the wireless key.

---

