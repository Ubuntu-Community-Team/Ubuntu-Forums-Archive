---
title: "Wammu - Sony Ericsson c510 mobile phone"
date: 2009-11-29
forum: General Help
---

### Post by David_UK on 2009-11-29
I'm following [_[COLOR="Blue"]these[/COLOR]_]("http://z0manifest.blogspot.com/2009/03/wammu-and-finding-usb-ports.html") steps for setting up Wammu.
However, after connecting via USB cable, and then choosing either USB mode or Phone mode, I run *hwinfo* but the results give variations of this:

*linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.10'*

I don't get any reference to */tty* at the end at all.
Ubuntu 9.04 knows the phone is there, F-Spot pops up as normal (I can access the phone memory and memory card through Nautilus.

In Wammu, I try combinations of /dev/ttyUSB... and /dev/ttyACM... but only get the "does not exist" error.

Any ideas?  Thanks

---

### Post by David_UK on 2009-11-29
Forget that - found an entry of /dev/ttyACM0, but it's not really clear at all - anyhow it worked in Wammu - but I'm sure I tried that before - dunno what's going on!

---

