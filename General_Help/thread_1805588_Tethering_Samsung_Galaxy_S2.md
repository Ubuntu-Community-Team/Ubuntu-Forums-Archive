---
title: "Tethering Samsung Galaxy S2"
date: 2011-07-16
forum: General Help
---

### Post by dhkillian on 2011-07-16
Just upgraded to 11.04 and got myself a Samsung Galaxy S2. 

Tried connecting via USB in order to sync contacts, photos etc. Got the error: 
"Unable to mount SAMSUNG_Android Error initialising camera: -60: Could not lock the device" 

Wanted to use the USB storage and USB tethering, so I enabled USB debug mode. So did this on the phone: 

Settings > Applications > Development > USB Debugging

Ubuntu can't see the phone. Then tried:

Settings > Wireless and Network > Tethering and Portable Hotspot Settings > USB Tethering.

Still no joy. Typing "lsusb" in terminal gives me:

derek@derek-Vostro-200:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 04e8:685e Samsung Electronics Co., Ltd 
Bus 002 Device 004: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 002: ID 050d:615a Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So it sees it in lsusb, but nowhere else, so I still can't copy and sync etc.

Anyone come across this problem, and if so, how were you able to solve it.

Kind regards

DHK

---

