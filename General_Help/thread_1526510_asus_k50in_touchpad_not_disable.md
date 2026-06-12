---
title: "asus k50in touchpad not disable"
date: 2010-07-08
forum: General Help
---

### Post by ardunarda on 2010-07-08
Hello i use ubuntu 10.04. Everything works great, however i can not figure out how to disable my touch-pad. Yet my touch-pad features works properly such as double tapping, triple tapping or scroll. I have tried everything at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) (most of them is for synaptic touchpad but mine is elantech)
here is the mine X11


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

thanks for help

---

### Post by ardunarda on 2010-07-08
up

---

### Post by mornings11 on 2010-07-08
sorry, same issue here. looking for help..thanks`

---

### Post by ardunarda on 2010-07-09
up

---

### Post by ardunarda on 2010-07-10
up

---

### Post by ardunarda on 2010-07-10
good solution found at fourth post [http://swiss.ubuntuforums.org/showthread.php?t=1333961](http://swiss.ubuntuforums.org/showthread.php?t=1333961)

---

