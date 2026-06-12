---
title: "can't remove linux-headers"
date: 2012-09-03
forum: General Help
---

### Post by The_Master_One on 2012-09-03
Hello everybody!
Few days ago I upgraded Ubuntu to 12.04 version. During update installation i recived a message "System problem detected". it refers to linux-headers-2.6.32-37. I tried to remove it but I get an error

unable to securely remove '/usr/src/linux-headers-2.6.32-37/drivers/gpu/drm/ttm/Makefile': Not a directory
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me to remove or fix this header
Thanks!

---

### Post by kimberlite on 2012-09-03
Try: ```
sudo apt-get autoremove
``` from a terminal.

---

### Post by The_Master_One on 2012-09-03
allready did, doesn't work

---

### Post by The_Master_One on 2012-09-03
I even tried to remove it manually, also didn't make it. It says that flder is owned by root and I can delete it even I have administrator privledges.

---

