---
title: "Removing Nvidia"
date: 2011-03-05
forum: General Help
---

### Post by Quarkrad on 2011-03-05
Running 10.10.  My graphics card has just blown up so I've had to switch to the motherboard internal graphics.  Problem is, Ubuntu doesn't like it - I have to start in recovery mode and 'low graphics for this sesion'.  How do I remove all 'knowledge' of Nvidia and then let Ubuntu configure itself for my new(!) graphics capability?

---

### Post by davidmohammed on 2011-03-05
try

```
sudo apt-get remove nvidia*

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

reboot

---

