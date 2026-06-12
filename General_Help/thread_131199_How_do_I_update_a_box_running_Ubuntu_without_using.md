---
title: "How do I update a box running Ubuntu without using a network connection?"
date: 2006-02-15
forum: General Help
---

### Post by PoiDog on 2006-02-15
I installed Ubuntu 5.10 on a desktop PC, but it has no internet connection.  However, I do have a laptop running WinXP with a high-speed connection.  

Is there a way to download files onto my WinXP laptop for updating my desktop running Ubuntu?

Also, is there a similar procedure for installing VLC or mplayer?

By the way, I have a USB drive that works on both systems.

Thanks

---

### Post by nanotube on 2006-02-16
well, as a crude method, you could just download the appropriate .deb files for the packages you want to install from the repositories, transfer them onto your ubuntu comp, and install them using command 
```
dpkg -i packagename.deb
```

but maybe someone can come up with a better way...

---

