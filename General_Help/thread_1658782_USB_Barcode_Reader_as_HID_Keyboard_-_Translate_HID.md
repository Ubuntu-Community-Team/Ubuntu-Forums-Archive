---
title: "USB Barcode Reader as HID Keyboard - Translate HID Events?"
date: 2011-01-03
forum: General Help
---

### Post by N.Maas on 2011-01-03
Hello there,

first I want to add the special problem on this subject as I'm not using Ubuntu but OpenWRT 10.03 on this project, but as none other forum seemded to help me out, I want to try here. (Sorry!)

So, I got an Datalogic Magellan 1100i with USB Cable and therefor configured to USB Keyboard. 

Dmesg:
usb 2-1: new full speed USB device using ohci_hcd and address 7 
usb 2-1: configuration #1 chosen from 1 choice 
input: Datalogic Scanning, Inc. Point of Sale Handable Scanner as  /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2 
generic-usb 0003:05F9:2602.0007: input: USB HID v1.11 Keyboard  [Datalogic Scanning, Inc. Point of Sale Handable Scanner] on  usb-0000:00:02.0-1/input0 

The Scanner get successfully recognized as HID and does generate Data on /dev/input/event0. But only HID Binary Stuff.

How do I "translate" these HID Events into "Plaintext"?

My Computers are embeeded Systems with OpenWRT and therefor can't support an window manager (they didn't got that speed, memory, graphicscard etc...).

What I need would be just and possibilty to pipe the Plaintext Codes to my Software...

Thank you very much,

Nico

---

