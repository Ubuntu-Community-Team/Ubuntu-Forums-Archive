---
title: "External HDD problems (not automounting usb drive)"
date: 2009-12-21
forum: General Help
---

### Post by Neezer on 2009-12-21
I have a 160GB WD external drive. When I plug it into my laptop with 9.04 on it I have no problems. It autodetecs and I can fire it right up. When I plug it into my computer with 9.10 on it it doesn't do anything, and I can't see it.

---

### Post by dcstar on 2009-12-22
> **Neezer said:**
> I have a 160GB WD external drive. When I plug it into my laptop with 9.04 on it I have no problems. It autodetecs and I can fire it right up. When I plug it into my computer with 9.10 on it it doesn't do anything, and I can't see it.

Run this when you plug it in and post the output:

```
dmesg
```

---

### Post by Neezer on 2009-12-22
I am assuming that you want just the end part of the output...There is a LOT of stuff above this that I am not sure if you need it or not. I guess it is recognizing that I have plugged in a device though which it good.

I actually did plug it in and take it out a few times. So that is why it says disconnect in there.

```

[ 1740.332449] usb 1-2.1: new high speed USB device using ehci_hcd and address 5
[ 1740.453313] usb 1-2.1: configuration #1 chosen from 1 choice
[ 1795.397993] usb 1-2.1: USB disconnect, address 5
[ 1810.960400] usb 1-2.1: new high speed USB device using ehci_hcd and address 6
[ 1811.052599] usb 1-2.1: configuration #1 chosen from 1 choice

```

---

### Post by Neezer on 2009-12-23
Bump! Still can't get it...not as big of an issue now as I did an scp command from my lappy to the server to put 80GB of music onto the server....took a while, but accomplished the task. I would still like to get this going.

---

### Post by dcstar on 2009-12-24
> **Neezer said:**
> I am assuming that you want just the end part of the output...There is a LOT of stuff above this that I am not sure if you need it or not. I guess it is recognizing that I have plugged in a device though which it good.

I actually did plug it in and take it out a few times. So that is why it says disconnect in there.

```

[ 1740.332449] usb 1-2.1: new high speed USB device using ehci_hcd and address 5
[ 1740.453313] usb 1-2.1: configuration #1 chosen from 1 choice
[ 1795.397993] usb 1-2.1: USB disconnect, address 5
[ 1810.960400] usb 1-2.1: new high speed USB device using ehci_hcd and address 6
[ 1811.052599] usb 1-2.1: configuration #1 chosen from 1 choice

```

I would surmise that the USB port cannot provide enough power for the device.

See if there is a BIOS option to change the USB, or move any other USB devices to ensure that the external drive is the only thing drawing power from that controller.

---

