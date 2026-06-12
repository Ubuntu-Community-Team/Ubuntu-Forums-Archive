---
title: "Network manager wont recognize wired network otherwise functional on other notebook"
date: 2010-12-23
forum: General Help
---

### Post by Laser Topalovic on 2010-12-23
Network manager wont recognise wired network on asus f7l notebook in 8.10 nor 10.04 versions, otherwise its fully functional on other notebook, via which I am connected in da moment. Please give a suggestion. Thanks

---

### Post by slooow on 2010-12-23
```
lspci | grep Ethernet
```
should give you the model of the NIC
Then find the module (driver) for it.

---

