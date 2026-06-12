---
title: "GDM Won't Automatically Start After Boot"
date: 2010-10-30
forum: General Help
---

### Post by Palike on 2010-10-30
first thing: big sorry for my english

hi i have acer aspire 5935G with ubuntu 10.10. i do this with my boot screen
[http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/) 

after that when i run ubuntu its boot me in command line i think its something like telinit 3.
when i write sudo gdm service start:
Failed to acquire org.gnome.DisplayManager
Could not acquire name; bailing out

when i write startx, there was a few warnings, fatal error and this Please also check the log file at "/var/log/Xorg.0.log" for additional information. 

also i instal nvidia driver
[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)
 and when i try run nvidia x server setings there was this
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
i try sudo nvidia-xconfig but its not help to me.... anyone can help me?... :-$

---

