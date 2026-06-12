---
title: "Ati Driver help!"
date: 2006-04-05
forum: General Help
---

### Post by yellow beard on 2006-04-05
Okay so ive installed the driver fine but when i try to run  "/usr/X11R6/bin/aticonfig --initial" to configure i get the error: 

error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

also when trying to install the new firefox i get the same error but its missing libstdc++.so.5.

Can some please tell me how to get these files!

---

### Post by gerbman on 2006-04-06
[QUOTE=yellow beard]Okay so ive installed the driver fine but when i try to run  "/usr/X11R6/bin/aticonfig --initial" to configure i get the error: 

error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

also when trying to install the new firefox i get the same error but its missing libstdc++.so.5.

Can some please tell me how to get these files![/QUOTE]What video card do you have? [This]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") tutorial works for installing drivers for 8500+ and x-series ATI cards. If you have already installed these drivers, you can reconfigure the X server with either ```
sudo dpkg-reconfigure xserver-xorg
```or```
sudo fglrxconfig
```If you just want to install libstdc++.so.5, do the following```
sudo apt-get install libstdc++5
```

---

### Post by yellow beard on 2006-04-06
Awesome thanks alot.

---

### Post by yellow beard on 2006-04-06
Ive got it installed correctly. But the refresh rates are killing me. How do you configure it so you can add more?

---

### Post by gerbman on 2006-04-06
[QUOTE=yellow beard]Ive got it installed correctly. But the refresh rates are killing me. How do you configure it so you can add more?[/QUOTE][This]("http://ubuntuforums.org/showthread.php?t=83973") is a very popular how-to for doing that. Cheers!

---

### Post by yellow beard on 2006-04-06
Cheers.

---

