---
title: "How can I change Ubuntu logo at boot."
date: 2010-09-01
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-09-01
How can I change Ubuntu logo at boot, I am Using Ubuntu Lucid 10.04

---

### Post by garvinrick4 on 2010-09-01
Go into synaptics and type in "plymouth" choose another like "solar" and choose to install it. 

Open a terminal.

```
sudo update-alternatives --config default.plymouth 
```
Choose solar then:
```
sudo update-initramfs -u
```
```
sudo update-grub
```

reboot:

---

### Post by Lukasz Tarkowski on 2010-09-01
Thank you garvinrick4

---

