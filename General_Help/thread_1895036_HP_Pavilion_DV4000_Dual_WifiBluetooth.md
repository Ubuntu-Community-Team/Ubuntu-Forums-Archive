---
title: "HP Pavilion DV4000 Dual Wifi/Bluetooth"
date: 2011-12-13
forum: General Help
---

### Post by jfreak53 on 2011-12-13
I have a HP, the title states what it is.  It has a wifi card that has integrated Bluetooth in it.  I have the wifi working great, the bluetooth I know works since it worked in Windows before.  But Ubu doesn't even detect it, any thoughts?

---

### Post by LowSky on 2011-12-14
open a terminal

use this command... i think....

```
sudo /etc/init.d/bluetooth restart
```

see this

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by jfreak53 on 2011-12-15
Yeah I've checked a couple times and followed the tutorial a couple also, uninstalling and re-installing just to make sure.  All the bluetooth packages are installed and up to date right now and have been for quite some time.  But still no BT, when I restart Bluetooth services it restarts fine, but if I list BT devices I get 0 listing of devices.

Running both commands:

> lshw | grep Bluetooth -A15
hciconfig

I get nothing returned.

Now I did get this output showing bluetooth, but I think they are just general drivers:

> dmesg|tail
[   26.897104] type=1400 audit(1323947368.049:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1110 comm="apparmor_parser"
[   28.216087] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   32.731400] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   33.208024] ham0: no IPv6 routers present
[   33.656020] eth1: no IPv6 routers present
[   75.308296] exe (1971): /proc/1971/oom_adj is deprecated, please use /proc/1971/oom_score_adj instead.
[ 1512.250357] Bluetooth: Core ver 2.15
[ 1512.250398] NET: Registered protocol family 31
[ 1512.250400] Bluetooth: HCI device and connection manager initialized
[ 1512.250403] Bluetooth: HCI socket layer initialized

Thanks for the help.

---

### Post by jfreak53 on 2011-12-17
Any thoughts?

---

### Post by jfreak53 on 2011-12-18
The Wireless card with the integrated Bluetooth seems to be an:

Intel Corporation PRO/Wireless 2200BG

Driver "ipw2200" is used from what I understand.

---

### Post by jfreak53 on 2012-01-03
Any thoughts?

---

