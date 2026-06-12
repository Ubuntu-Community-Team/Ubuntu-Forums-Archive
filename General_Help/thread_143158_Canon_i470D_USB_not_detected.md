---
title: "Canon i470D USB not detected"
date: 2006-03-11
forum: General Help
---

### Post by mgchan on 2006-03-11
I attach the printer and here is what I get from dmesg:
```
[4311446.817000] usb 2-3: new full speed USB device using ohci_hcd and address 12
[4311446.916000] hub 2-3:1.0: USB hub found
[4311446.921000] hub 2-3:1.0: 3 ports detected
[4311447.197000] usb 2-3.1: new full speed USB device using ohci_hcd and address 13
[4311447.268000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 13 if 0 alt 0 proto 2 vid 0x04A9 pid 0x107C
[4311447.413000] usb 2-3.2: new full speed USB device using ohci_hcd and address 14
[4311457.462000] usb 2-3.2: string descriptor 0 read error: -110

```

I'm not sure what that last error means - maybe it's the reason I can't detect the printer?

I restarted cupsys with sudo /etc/init.d/cupsys restart

However when I go to New Printer in my Printers settings nothing is there.

I read online that I can use the BJC-7000 driver with this but manually adding the printer doesn't work.

Anyone know how I can troubleshoot this?

---

