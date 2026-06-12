---
title: "How to bring back compiz?"
date: 2010-05-03
forum: General Help
---

### Post by hkl8324 on 2010-05-03
To make in short,
What I have done:

1.Intalled 9.10 on a sysytem with intel core i3 CPU/GPU (Compiz Worked out of the box with i3 GPU)
2.Bought a nvidia Geforce GT240 card, intalled the proprietry driver on Ubuntu 9.10 download form nvidia.com (Compiz Worked with GT240)
3.Updated Ubuntu to 10.04
4.Dont know how to kill x in 10.04 (sudo /etc/init.d/gdm stop wont work anymore...) so I installed the nvidia driver from System>Administration>Restricted Driver  (Compiz Worked with GT240)
5.Removed and selled the GT 240 on somesite like ebay because its profromance in on par with Windows Games...
6.Removed the proprietry driver and disabled "Restriced Driver"
7.Deleted the xorg.conf file (the system regenrate an empty file after reboot)
8.Reboot and use back my onn CPU GPU (Compiz Wont work anymore)

hkl8324@hkl8324-desktop:~$ glxinfo |grep direct
Xlib:  extension "GLX" missing on display ":0.0".

lsmod says I am using the i915 driver

---

