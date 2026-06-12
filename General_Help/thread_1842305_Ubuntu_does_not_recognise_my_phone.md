---
title: "Ubuntu does not recognise my phone"
date: 2011-09-11
forum: General Help
---

### Post by rdh61 on 2011-09-11
Hi,

I am running Ubuntu 10.10 on a desktop and 10.04 on a laptop. Neither recognises my LG KU990 phone when connected with a USB cable. It is recognised on Windows XP.

Is there anything I can do to remedy this?

Many thanks.

---

### Post by raja.genupula on 2011-09-11
```
lsusb
```

shows is your phone connected properly to the system or not .
look the output of that command

---

### Post by rdh61 on 2011-09-12
robert@robert-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 125f:c03a A-DATA Technology Co., Ltd. 
Bus 001 Device 002: ID 0d49:7450 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But it is not listed in "Places" or "Disk Utility". How can I access it?

Thanks for any answers.

---

### Post by 5ynic on 2011-09-12
I had a similar problem, and it worked when I used the USB port at the back of the PC instead of the ones at the front/sides.

---

### Post by cottfcfan on 2011-09-12
I had a similar problem with a Samsung phone.
I had to change a setting on the phone so Ubuntu could see it as a mass storage device.
Could be something similar.

---

### Post by raja.genupula on 2011-09-12
> **rdh61 said:**
> robert@robert-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 125f:c03a A-DATA Technology Co., Ltd. 
Bus 001 Device 002: ID 0d49:7450 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But it is not listed in "Places" or "Disk Utility". How can I access it?

Thanks for any answers.

that shows your phone connected . in your phone settings check for what the mode you have selected for USB connectivity .

---

