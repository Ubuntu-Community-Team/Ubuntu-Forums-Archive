---
title: "natty wil not shutdown from panel menu"
date: 2011-08-22
forum: General Help
---

### Post by cybergalvez on 2011-08-22
Hi all, I am running natty (64bin) and recently it has stopped responding to either the shutdown or reboot command from the panel menu. When you select shutdown, and then hit yest to confirm, nothing happens. I looked at the logs and nothing seems to be generating any errors either. 

Not even sure how to trouble shoot this issue. Any help is appreciated.

Jose

---

### Post by TeoBigusGeekus on 2011-08-22
As a temporary measure, try
```
sudo shutdown -h now
```
to shutdown and
```
sudo reboot 
```
to reboot.

---

