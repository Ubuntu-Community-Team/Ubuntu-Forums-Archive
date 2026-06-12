---
title: "Help with a corrupted USB pendrive"
date: 2012-09-16
forum: General Help
---

### Post by stubblepoo on 2012-09-16
I was moving saves from one xbox to another on a normal USB which had be formatted via the xboxes. I shut down the xbox it was in, removed the stick and then later that day tried it with my Win7 lappy. It didn't have the usual hidden xbox folder but some folders with weird corrupted symbols as names, thought nothing of it, assumed I'd just reformat it later when I next needed it. Now I need it and the weird thing is this: When plugged in it really quickly mounts and unmounts, like 1 sec bursts of each, it doesn't mount or even show under fdisk in ubuntu.


thoughts? 

Cheers Spoo

---

### Post by cogier on 2012-09-16
Have a look at the drive with Gparted which is in the Software Centre.

You may be able to format it there but be VERY careful that you format the correct drive.

---

### Post by stubblepoo on 2012-09-16
yeah it doesn't show in gparted either. The light on the USB is flashing so something is happening. Looks like its a write off.

---

### Post by Epodx64 on 2012-09-16
Plug in the pendrive and from a terminal type:

lsusb

and post it back please.

---

### Post by stubblepoo on 2012-09-17
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ca:1841 Ricoh Co., Ltd Fujitsu F01/ Lifebook U810 [R5U870]
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 002: ID 0430:0530 Sun Microsystems, Inc. 
Bus 004 Device 002: ID 0c24:000f Taiyo Yuden Bluetooth Device (V2.0+EDR)
Bus 001 Device 041: ID 154b:0043 PNY 


The final line is the relevant usb drive. So its being seen but not accessed?

---

