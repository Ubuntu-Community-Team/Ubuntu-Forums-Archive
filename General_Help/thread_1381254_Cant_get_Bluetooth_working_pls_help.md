---
title: "Cant get Bluetooth working pls help"
date: 2010-01-14
forum: General Help
---

### Post by Bloemetjesgordijn on 2010-01-14
Hi guys,

I had to uninstall HIDPOINT (a Bluetooth driver) because the upgrade failed.

Now my Bluetooth Keyboard and Mouse are not working. I reinstalled both KBluetooth and Bluetooth Manager...both not working:(

It seems that the BlueTooth dongle is not recognized. (In BIOS it is working!!)

please help me, I am lost here

lsusb output:
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 007: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 005 Device 003: ID 0403:fc60 Future Technology Devices International, Ltd
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

hcitool scan output:
```
Device is not available: No such device
```
hcitool dev output
```
Devices:
```

config:
KUbuntu 64bits
Kde 4.3.4
KeyBoard & Mouse: Logitech DiNovo Edge

Thx in advance 

Kind regards,

Bloemetjesgordijn

---

