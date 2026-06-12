---
title: "Can't receive files via bluetooth"
date: 2009-11-29
forum: General Help
---

### Post by Poyntz on 2009-11-29
I had some trouble receiving files via KBluetooth 0.4, 
Related to KDE 4.3.2, Ubuntu 9.10

Basically, simple fix:
1. ```
sudo apt-get install obexpushd
```
(ie, install the obexpushd package)

The bug:
- I think there's something wrong with the package **obex-data-server**. 

That said, KBluetooth should send files (just might not receive files without obexpushd)

---

