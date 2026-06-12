---
title: "Driver troubles with USB/serial port interface cable"
date: 2011-07-18
forum: General Help
---

### Post by tajasel on 2011-07-18
Hi there,

I have a Garmin eTrex Camo GPS unit, and the cable for it has a serial port, so I purchased a QinHeng Electronics HL-340 USB-Serial adapter online, assured by a Linux-using friend that it would work - and indeed, my netbook recognises that the cable exists, but is not picking up the cable (and GPS device) on the other end of the adapter.

Here's what I get running [FONT="Courier New"]lsusb[/FONT]:

```
tajasel@epie:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 018: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The serial cable did come with a mini driver CD but being that I have a netbook and no external CD drive, I can't use it; I wonder if the problem is caused by lack of driver, but have Googled away for the last 20 mins without turning up a Linux driver for the thing.

Help?! I'm going to San Francisco on Friday and really want to take my GPS with me so I can grab some international geocaches over there.

---

### Post by Cybie257 on 2011-07-18
Found this:

[http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/](http://tiagovaz.wordpress.com/2008/01/04/using-a-hl-340-usb-serial-adapter-against-2623-linux-kernel/)

-Cybie

---

### Post by tajasel on 2011-07-19
It seems that driver is too old for the kernel I'm using, and I can't find a newer one :/ does this mean I have no chance of getting it working? :/

---

