---
title: "Repeating USB messages in /var/log/messages"
date: 2006-03-12
forum: General Help
---

### Post by mgchan on 2006-03-12
While trying to troubleshoot my USB printer I found something interesting.  Every 30 seconds or so I get this repeating message in /var/log/messages

```
Mar 12 00:51:27 localhost kernel: [4294881.544000] scsi7 : SCSI emulation for USB Mass Storage devices
Mar 12 00:51:27 localhost usb.agent[10710]:      usb-storage: already loaded
Mar 12 00:51:27 localhost kernel: [4294881.695000] usb 2-3.3: new full speed USB device using ohci_hcd and address 40
Mar 12 00:51:33 localhost kernel: [4294888.212000] usb 2-3: USB disconnect, address 37
Mar 12 00:51:33 localhost kernel: [4294888.212000] usb 2-3.1: USB disconnect, address 38
Mar 12 00:51:33 localhost kernel: [4294888.213000] drivers/usb/class/usblp.c: usblp0: removed
Mar 12 00:51:33 localhost kernel: [4294888.215000] usb 2-3.2: USB disconnect, address 39
Mar 12 00:51:33 localhost kernel: [4294888.296000] usb 2-3: new full speed USB device using ohci_hcd and address 44
Mar 12 00:51:33 localhost kernel: [4294888.395000] hub 2-3:1.0: USB hub found
Mar 12 00:51:33 localhost kernel: [4294888.399000] hub 2-3:1.0: 3 ports detected
Mar 12 00:51:34 localhost usb.agent[10879]:      usbcore: already loaded
Mar 12 00:51:34 localhost kernel: [4294888.656000] usb 2-3.1: new full speed USB device using ohci_hcd and address 45
Mar 12 00:51:34 localhost kernel: [4294888.726000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 45 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107C
Mar 12 00:51:34 localhost kernel: [4294888.878000] usb 2-3.2: new full speed USB device using ohci_hcd and address 46
Mar 12 00:51:34 localhost usb.agent[10933]:      usblp: already loaded

```

This whole section will repeat, with incrementally higher "address" numbers.  Often when I start up the computer I get a bunch of errors with USB as well.  Is this likely a problem with my USB port?  I tried disabling it in BIOS and as expected the problems go away, but so does USB functionality.  The problem occurs whether I have the ports set to 1.1+2.0 or just 1.1 alone.

Anyone know what could cause this?  Should I just go buy a new card?

---

### Post by MountainX on 2008-03-26
I'm having this same issue with Hardy beta. Any advice?

---

