---
title: "Cant Set Resolution to 1920x1080"
date: 2011-08-05
forum: General Help
---

### Post by SkyPoweR on 2011-08-05
Hello,
I Bought a new screen today [ YAY ]
LG Flatron W2243T,
i searched over google like 2 hours and cant found nothing that works.
My Video Cars Is : nVidia 8500GT.

Tnx for help3rs.

---

### Post by realzippy on 2011-08-05
run 
```
sudo nvidia-xconfig
```
reboot or restart Xserver,if it still not works,
edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
change the Hsync and Vrefresh values (Monitor section)
to the valid values for your monitor model(manual).

---

### Post by SkyPoweR on 2011-08-05
Tnx, After a lot of search, I've found my Hsync and Vrefresh,
Here's my xorg.conf [ for people with my screen who has the same prob ] :
first use "sudo nvidia-xconfig" and then change the Monitor section to mine.
> 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG Flatron W2243T"
    ModelName      "CRT-1"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection



Have Fun :)

---

### Post by realzippy on 2011-08-05
Hsync and Vrefresh,not whole monitor section.
Might be a problem if it is not CRT-1..
So set thread as solved..have fun!

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

