---
title: "Alcor Micro Corp. Hub 4ports"
date: 2011-03-03
forum: General Help
---

### Post by Orsb on 2011-03-03
Hi,

I have recently bought a PCMCIA USB2.0 4ports cardbus, but it does not work.  I also installed ndiswrapper, but it did not help

My computer runs:

Linux ubuntu 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

and with the command lsusb, I get the following details

Bus 004 Device 003: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I also tried sudo modprobe -r ehci_hcd

which resulted:
FATAL: Module ehci_hcd is builtin

Could anyone please advise me in this matter?

---

### Post by LowSky on 2011-03-03
ndiswrapper is for wifi cards. it will not do anything for a usb hub

try this:

open terminal and type

```
gksu gedit /etc/modules
```

that will open up a text file

add this to the text file
```
usb_modules
```

then reboot and see if it works

---

### Post by Orsb on 2011-03-03
I got the following error upon reboot:

ohci_hcd 0000:06:00.0 USB HC takeover failed (BIOS/SMM bug)
ohci_hcd 0000:06:00.0 can't setup
ohci_hcd 0000:06:00.0 init 0000:06:00.0 fail,- 16
ohci_hcd 0000:06:00.1 USB HC takeover failed (BIOS/SMM bug)
ohci_hcd 0000:06:00.1 can't setup
ohci_hcd 0000:06:00.1 init 0000:06:00.1 fail, -16
ehci_hcd 0000:06:00.2 startup error -19
ehci_hcd 0000:06:00.2 init 0000:06:00.2 fail -19

---

