---
title: "How do i uninstall proprietary ATI driver"
date: 2011-05-26
forum: General Help
---

### Post by ImDougy on 2011-05-26
I installed the proprietary ATI graphics driver from the AMD website(i did not install it using the additional drivers tool in the administration menu) and i don't know how to uninstall it. how do i do this?

---

### Post by TeoBigusGeekus on 2011-05-26
Was it a deb package, did you built it from source or something else?

---

### Post by Krytarik on 2011-05-26
Run these commands to remove the any remnants of the manually installed "fglrx" driver, and to restore the functionality of the "radeon" driver:
```

sudo /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
```The second one may output an error, but run it anyway, just to be sure.

Greetings.

---

### Post by ImDougy on 2011-05-29
thank you Krytarik the open source driver just runs smoother.

---

