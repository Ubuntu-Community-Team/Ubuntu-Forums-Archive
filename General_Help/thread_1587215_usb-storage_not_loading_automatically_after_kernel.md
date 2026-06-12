---
title: "usb-storage not loading automatically after kernel update"
date: 2010-10-03
forum: General Help
---

### Post by GhostCoder on 2010-10-03
Hi,

I just noticed that my USB sticks are not automatically mounted anymore after having updated kernel from 2.6.32-24-generic to 2.6.32-25-generic on my Acer Extensa 5220 laptop. It still works if I "sudo modprobe usb-storage". What might have gone wrong? I'm not experiencing this on my desktop machine also running 10.04. How to fix this permanently? And now I remember that I'm not able to use my mobile broadband either (Nokia N900 in PC Suite mode through USB). It's just not detected anymore. It must suffer from this same problem. I tried to roll back to the previous kernel, but then the restricted driver for my Broadcom WLAN refuses to install :(

---

### Post by GhostCoder on 2010-10-03
One problem more: need to remove and activate again the Broadcom restricted driver after every boot. What the hell happened? Everything worked like a dream before..

---

### Post by GhostCoder on 2010-10-03
Temporarily(?) fixed the usb-storage and automount issue by adding usb-storage to /etc/modules.

---

