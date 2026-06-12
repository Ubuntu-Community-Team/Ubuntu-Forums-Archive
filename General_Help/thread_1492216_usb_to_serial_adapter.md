---
title: "usb to serial adapter"
date: 2010-05-24
forum: General Help
---

### Post by evilducy on 2010-05-24
Hay all, not sure where to post this, so mods feel free to relocate..
I'm new to the forums, and Ubuntu/Linux in general. But have been kinda lurking for about a year. I am trying to install a Usb to serial adapter, and am having a few issues.

I run lsusb and get this.
> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device [COLOR=Red]119[/COLOR]: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303]
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
I also ran dmesg and cant actually past the response here, its that long... The basic gist is that I get well over 100 
 > hub 2-0:1.0: unable to enumerate USB device on port 2I found this
 > [http://jindroid.com/2010/02/05/how-to-set-up-usb-serial-cable-on-ubuntu/](http://jindroid.com/2010/02/05/how-to-set-up-usb-serial-cable-on-ubuntu/)But after I run dmesg I don't get the last lines.
 > usbcore: registered new interface driver pl2303
[191526.790299] pl2303: Prolific PL2303 USB to serial adaptor driverI'm running Lucid on a Acer laptop with a AMD Truion 64 chip-set, mk-36.

Not real sure where to go from here, I'm trying to run some tuning software for my bike using Wine. I'd rather not try to make the machine dual boot. Or does anyone have a suggestion other than Wine??

---

### Post by psytrox on 2010-09-26
I have that issue.  Nothing found to fix yet.

---

### Post by bilkay on 2010-10-06
What's the brand name of your adapter?

---

