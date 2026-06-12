---
title: "Screen resolution and EDID info"
date: 2010-05-01
forum: General Help
---

### Post by jonblund on 2010-05-01
Before I upgrade to 10.4 It would be nice to find the best solution to this problem. 
I use a KVM switch that dont pass the EDID info from the screen to the OS. 
To solve this, that is, to get the correct screen resolution, i need to pass monitor and screen info to the OS at every startup. 
One way is to ad a script to /etc/gdm/init/default, or in KDE /etc/kde4/kdm/Xsetup.
My question is: Anyone out there who knows a better way. For example have it set iin an earlier stage in the boot process.

---

### Post by jonblund on 2010-05-01
Just tested to Upgrade from kubuntu 9.10 to 10.4 an got a black screen probobly because the modified Xsetup file.

---

### Post by dino99 on 2010-05-01
black screen is something common with the actual xserver. The latest kernel have built-in video capabilities and most of issues are with old xorg.conf coming from dist-upgrading, so rename yours or delete it if you dont care, 10.04 dont need it by default

---

