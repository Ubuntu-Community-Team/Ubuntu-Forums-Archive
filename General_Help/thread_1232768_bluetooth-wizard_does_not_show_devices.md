---
title: "bluetooth-wizard does not show devices"
date: 2009-08-05
forum: General Help
---

### Post by vipseixas on 2009-08-05
I am trying to pair a bluetooth device with my Jaunty but it does not show when I run the bluetooth-wizard, but everything else seams fine:

```

$ lsusb
[...]
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
[...]

$ hcitool dev
Devices:
	hci0	00:1F:81:00:02:50

$ hcitool scan
Scanning ...
	00:11:67:81:03:74	BCK-08

```

  What may be wrong? Is there a way to pair the device without the bluetooth-wizard?

[]s!

---

