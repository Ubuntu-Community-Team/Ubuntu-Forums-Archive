---
title: "No X Server"
date: 2006-06-14
forum: General Help
---

### Post by mattm591 on 2006-06-14
Hi,
I managed to break Ubuntu!

I was trying to get XGL using the instrcutions here [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267) but I don't think I did it right and stupidly I made no back ups of the files i edited. Now whenever I load I get this message:

> GMD: xserver not found: /usr/bin/xgl/ :0 :0 --fullscreen -ac -accel glx:pb 
Error: command could not be exectured. 
Please install the X serer or correct GDM config and restrt GDM

Does anyone know how I can go back to regular X? Thank you :)

---

### Post by mattm591 on 2006-06-14
Never mind, all fixed.. just had to remove /etc/gdm/gdm.conf-custom and then of course restart... !

---

