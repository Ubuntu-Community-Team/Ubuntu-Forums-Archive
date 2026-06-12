---
title: "udev ignore_device won't work if device already connected"
date: 2009-09-15
forum: General Help
---

### Post by cmwslw on 2009-09-15
I'm trying to find out a way to simulate disconnecting a device from a software aspect, just as if a user physically disconnected it. So far I've made a udev rule in /etc/udev/rules.d called 5-nano.rules:
```
SYSFS{idVendor}=="05ac", OPTIONS+="ignore_device"
```
This rule works fine for ignoring devices, but only after they have been disconnected and reconnected. But what i want to do is to be able to write the rule, and then have the device ignored as if it were disconnected. I've tried "udevadm trigger" with and without sudo, but for some reason I cannot apply this rule while the device is connected. Any suggestions?

By the way, I am able to reconnect a device that has been ignored by removing 5-nano.rules, and then running "sudo udevadm trigger", but like said above, not the other way around. (for some reason my system time and internet get messed up when I run that command though)

Thanks in advance,
Cory

---

