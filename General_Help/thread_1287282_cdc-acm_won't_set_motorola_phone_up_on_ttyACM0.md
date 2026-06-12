---
title: "cdc-acm won't set motorola phone up on ttyACM0"
date: 2009-10-10
forum: General Help
---

### Post by tim22b on 2009-10-10
First, if this is in the wrong forum, please move it.  I was unsure about its proper place.  Second, this is on 9.04, 2.6.28-15-generic kernel, 32 bit system.

I'm trying to get my phone to work with moto4lin.  It's a VU30.  I realize it's not given under the supported list for moto4lin but I figured since it works with p2kcommander in windows, it's probably a p2k device and might work with moto4lin.  I figured I'd ask here before attempting to install motorola phone tools stuff on cxoffice or wine.

So the problem is the phone is being mounted or attached or whatever the proper term is to /dev/ttyACM0 or any of other locations it might be in.

After some searching and trying a few methods I realized I had to do modprobe cdc-acm to even get it to say anything about acm.

I'm still stuck in the same situation.  lsusb gives
```

Bus 001 Device 002: ID 13fd:1040 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0a48:3239 I/O Interconnect Multimedia Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 22b8:2c64 Motorola PCS 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

which, if I understand it correctly, means the usb driver is properly seeing it.

The result of modprobe cdc-acm (from dmesg) is

```

[27216.688782] usbcore: registered new interface driver cdc_acm
[27216.688789] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```

The problem however is that when I plug in the phone I only get this (from dmesg as well)

```

[27384.528030] usb 2-3: new full speed USB device using ohci_hcd and address 3
[27384.761889] usb 2-3: configuration #1 chosen from 1 choice

```

moto4lin looks like it recognizes it as an AT device and pulls the vendor and product IDs from it, however when it tries to put it into P2K mode it says the device is disconnected (which I'm guessing is because it's looking for /dev/ttyACM0 as the device).

Thanks

edit: It should show some kind of message saying it set up the phone on ttyACM0 if it's working properly (and ttyACM0 should exist for that matter).

---

### Post by tim22b on 2009-10-10
Someone's got to have an idea at least.

---

### Post by htm316 on 2009-10-22
I think if you can see ttyACM0 then that means the cdc-acm driver was already loaded and detected the phone. You can now use the ttyACM0 to send AT commands to your phone.

---

### Post by skippuff54 on 2009-12-16
Please see my posts:

[http://ubuntuforums.org/showthread.php?t=1162437]("http://ubuntuforums.org/showthread.php?t=1162437")

[http://ubuntuforums.org/showthread.php?t=1163204]("http://ubuntuforums.org/showthread.php?t=1163204")

I also filed a bug report in Launchpad, which is linked in the first of those.

---

### Post by 21jeremy21 on 2010-01-24
I had issues for hours getting my k1 to work with moto4lin despite following the [wiki]("http://moto4lin.sourceforge.net/wiki/KRZR_K1") and [URL="http://moto4lin.sourceforge.net/wiki/KRZR_K1-HELP"]help page
[/URL]

the phone was showing up as /dev/sg2 and /dev/sdb and I was getting an error that said something about " device temporarily unavailable" when I tried to switch to p2k

this turned out to be because a setting in the phone (Settings->Connection->USB Connection->Default Connection) needed to be changed to "Data Connection" instead of "Memory card".

It's also worth mentioning that the "P2k Product ID" (in moto4lin preferences) needs to be set to one less than the "AT Product ID". This is as per the wiki page, but I didnt notice at first.

Moto4lin is now working perfectly with my K1 .

---

