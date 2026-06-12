---
title: "Epson 3590 scanner stopped working after some updates"
date: 2009-08-17
forum: General Help
---

### Post by n1wil on 2009-08-17
Hi,

I'm really in a bind.  For a LONG time, my Epson 3590 scanner was working flawlessly with Sane.  I am using Ubuntu 8.04 LTS.  Just recently, I applied some updates (cannot remember what they were, I just completed them).  After the updates (a couple kernels too later I believe), my scanner no longer works.  Launching Sane gives the following error:

Failed to open device `snapscan:libusb:005:006': Invalid argument

This is VERY frustrating, I've searched everywhere and can't seem to find resolution on this issue.  One thread elsewhere had me searching for a firmware file that was supposed to be in /usr/share/sane/snapscan but the snapscan directory in this path does not exist.  I tried on other Ubuntu machines and I get the same problem.  I know the scanner works, I just tried it on a Windows machine and no problems with it.  

The issue is, I have no Windows machines in this location  and I'm screwed because I am now without a working scanner which was previously working on Ubuntu systems.  I have 4 machines running Ubuntu >= 8.04 and none of them work with this USB scanner anymore.  Can anyone please help shed some light on this?

An interesting thing to note is that when the USB plug is not plugged in, the green light is lit solidly.  When I plug in the USB cable, the green light flashes a couple times then goes out.  here is the dmesg output from that event:

[  801.747529] usb 5-3: new high speed USB device using ehci_hcd and address 6
[  801.887244] usb 5-3: configuration #1 chosen from 1 choice

When i run scanimage -L here is the output:

scanimage -L
device `snapscan:libusb:005:006' is a EPSON EPSON Scanner flatbed scanner

When i type scanimage with no arguments, here is what I get:

[snapscan] download_firmware: No firmware entry found in config file snapscan.conf.
scanimage: open of device snapscan:libusb:005:006 failed: Invalid argument


Please help...   thanks.

---

