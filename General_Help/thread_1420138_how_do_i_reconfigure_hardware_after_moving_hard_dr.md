---
title: "how do i reconfigure hardware after moving hard drive to new laptop?"
date: 2010-03-02
forum: General Help
---

### Post by mmoalem on 2010-03-02
hi there all - have moved my hard drive from one laptop to another (gateway to vaio) - i fully expected to need to reinstall ubuntu but it seems to work fine except for couple of hardware issues (for example id does not recognise the ethernet cable puged to the docking station)
any idea how i do i reconfigure so it looks for the hardware again and install the relevent bits?

---

### Post by pbrane on 2010-03-02
As far as your ethernet is concerned, udev has named the device it found on the gateway as eth0. The MAC address is in the naming rule. My guess is that when you moved the HD to the vaio your ethernet is now eth1. If you look in */etc/udev/rules.d/70-persistent-net.rules* you'll find the MAC address for "eth0" and most likely a second rule for "eth1". Maybe even a rule for your wireless. If you copy the eth1 MAC address to the eth0 rule, comment out the eth1 rule, and then type */etc/init.d/networking restart* in a terminal you should be fine. This is a snippet of my rules file.
```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="**00:1d:09:e4:76:a1**", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="**00:1c:fb:62:e8:14**", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

the numbers in bold are the MAC addresses of the hardware, in case you didn't already know.

---

