---
title: "Bluetooth and Apparmor messages during boot when not installed"
date: 2009-11-04
forum: General Help
---

### Post by hwttdz on 2009-11-04
I'm attempting to make my machine boot up a little quicker by removing a few unused apps, and I've attempted to remove apparmor, because it seems to not be really a production ready app and any bluetooth sort of things because I don't use bluetooth.  Anyways, doing dmesg still shows a few messages about both bluetooth and apparmor and I am wondering how to remove these and hopefully shave a tiny bit of time from boot.  

```
dmesg|grep -Ei "Apparmor|Bluetooth"
[    0.010000] AppArmor: AppArmor initialized
[    0.440006] Bluetooth: Core ver 2.15
[    0.440080] Bluetooth: HCI device and connection manager initialized
[    0.440140] Bluetooth: HCI socket layer initialized
[    0.490252] AppArmor: AppArmor Filesystem Enabled
[    0.785440] Bluetooth: L2CAP ver 2.13
[    0.785502] Bluetooth: L2CAP socket layer initialized
[    0.785567] Bluetooth: SCO (Voice Link) ver 0.6
[    0.785630] Bluetooth: SCO socket layer initialized
[    0.785718] Bluetooth: RFCOMM TTY layer initialized
[    0.785783] Bluetooth: RFCOMM socket layer initialized
[    0.785847] Bluetooth: RFCOMM ver 1.11
```

---

