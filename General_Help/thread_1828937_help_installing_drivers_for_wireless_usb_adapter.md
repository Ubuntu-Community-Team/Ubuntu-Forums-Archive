---
title: "help installing drivers for wireless usb adapter"
date: 2011-08-19
forum: General Help
---

### Post by grimmghost on 2011-08-19
hi im trying to install the RTL8192CU_linux_v3.0.2164.20110715 drivers so my new wireless adapter works, but I have hit a wall when trying to insert the drivers after makeing them its telling me 

"-VGN-NS325J:~/wifi/driver/8188$ insmod 8192cu.ko
insmod: error inserting '8192cu.ko': -1 Operation not permitted


can anybody help me to get past this?

---

### Post by grimmghost on 2011-08-21
so I suppose it just isn't possible? or is it so simple that nobody want to help me out?

---

### Post by Cpierce on 2011-08-21
see if this helps 

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)

---

### Post by 3rdalbum on 2011-08-21
> **grimmghost said:**
> hi im trying to install the RTL8192CU_linux_v3.0.2164.20110715 drivers so my new wireless adapter works, but I have hit a wall when trying to insert the drivers after makeing them its telling me 

"-VGN-NS325J:~/wifi/driver/8188$ insmod 8192cu.ko
insmod: error inserting '8192cu.ko': -1 Operation not permitted


can anybody help me to get past this?

You're running this command as an ordinary user. For security reasons, an ordinary user can't insert kernel modules (such as drivers).

If you preface that command with the *sudo* command, it runs the command as Root (administrator). Only Root has the permissions to do these kinds of system-wide changes.

```
sudo insmod 8192cu.ko
```

I think the "insmod" command just allows the driver to load without you having to reboot anyway, so if you've rebooted your computer since yesterday you should already have the module loaded.

---

### Post by grimmghost on 2011-08-22
thanks a lot for the help. I installed the driver but cant seem to get the damned wifi adapter to register.... might be my fault for going for the 7 dollar adapter though.

---

### Post by grimmghost on 2011-08-22
the device is showing up (thanks to the help I have got here) but it says that its disabled by hardware switch.... the reason i was going with the usb wireless was because the switch broke off the board when my computer got dropped, was hoping this would bypass.

looks like its time to find a soldering iron and hardwire the wireless switch to on.

again thanks a ton for the help.:D

---

