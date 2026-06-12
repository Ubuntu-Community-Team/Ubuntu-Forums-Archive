---
title: "usb-storage.ko Kernel-mod doesn't load."
date: 2011-04-22
forum: General Help
---

### Post by DaveS4 on 2011-04-22
yea,just that. My usb storage kernel mod doesn't load. 
I was wondering if anyone could tell me how to get it to work.

---

### Post by karthick87 on 2011-04-22
With your USB device plugged in. Post the output of 

```
lsusb
```

---

### Post by DaveS4 on 2011-04-22
> **karthick87 said:**
> With your USB device plugged in. Post the output of 

```
lsusb
```

It recognizes devices, and they show up in lsusb. But the devices don't function. Here's the output of lsusb with my HTC phone connected....

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bb4:0ca5 High Tech Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by tredegar on 2011-04-22
**sudo modprobe usb_storage** should load it.

Which version of ubuntu are you running? What do you think you did do to stop it behaving normally?

---

### Post by DaveS4 on 2011-04-22
> **tredegar said:**
> **sudo modprobe usb_storage** should load it.

Which version of ubuntu are you running? What do you think you did do to stop it behaving normally?

I'm running 10.10, and it's been acting this way since I installed ubuntu. That was about 3 weeks ago. I'm new to ubuntu.

---

### Post by tredegar on 2011-04-23
Perhaps the install went wrong somehow. Have you applied the updates?

Is USB storage usable after you have loaded the **usb_storage** module?

---

### Post by DaveS4 on 2011-04-23
> **tredegar said:**
> Perhaps the install went wrong somehow. Have you applied the updates?

Is USB storage usable after you have loaded the **usb_storage** module?

I guess thats possible. I always allow updates (every day or two). 

How do I load the usb_storage module??

---

