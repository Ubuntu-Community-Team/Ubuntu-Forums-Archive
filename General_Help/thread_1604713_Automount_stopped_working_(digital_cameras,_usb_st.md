---
title: "Automount stopped working (digital cameras, usb sticks)"
date: 2010-10-24
forum: General Help
---

### Post by stringarray on 2010-10-24
I'm running ubuntu 10.04 and suddenly when plugging my cameras or usb sticks, they don't automount anymore, but they did before. 

What changed is last days I tried to build and install nautilus-sendto manually from source, and it required dependencies including GTK+3.0 (unstable), I don't know what happened exactly or if my system is broken, because some of this packages built and installed fine and others failed. If someone wants to help with that to get my installation to its original state it would be awesome.

I could mount my usb stick installing usbmount, it worked, but I didn't need this before.

What I want now is to mount my cameras: here is the output for:

```
lsusb 
gvfs-mount -l 
dmesg | tail -20
```
```

$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 022: ID 04a9:318f Canon, Inc. 
Bus 001 Device 019: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 018: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$ gvfs-mount -l
Volume(0): cdrom0
  Type: GUnixVolume
$ dmesg | tail -20
[174734.434063] eth2: unregister 'rndis_host' usb-0000:00:10.4-4.4, RNDIS device
[255473.347351] usb 1-4: USB disconnect, address 3
[255473.347357] usb 1-4.3: USB disconnect, address 4
[255473.347429] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: can't reset device, 0000:00:10.4-4.3/input0, status -108
[255475.292035] usb 1-4: new high speed USB device using ehci_hcd and address 18
[255475.424717] usb 1-4: configuration #1 chosen from 1 choice
[255475.425456] hub 1-4:1.0: USB hub found
[255475.425710] hub 1-4:1.0: 4 ports detected
[255475.696187] usb 1-4.3: new low speed USB device using ehci_hcd and address 19
[255475.792096] usb 1-4.3: configuration #1 chosen from 1 choice
[255475.796582] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:10.4/usb1/1-4/1-4.3/1-4.3:1.0/input/input8
[255475.796757] generic-usb 0003:0458:003A.0004: input,hidraw2: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:10.4-4.3/input0
[308799.276097] usb 1-4.4: new high speed USB device using ehci_hcd and address 20
[308799.370734] usb 1-4.4: configuration #1 chosen from 1 choice
[309099.103991] usb 1-4.4: USB disconnect, address 20
[309226.788218] usb 1-4.4: new high speed USB device using ehci_hcd and address 21
[309226.882494] usb 1-4.4: configuration #1 chosen from 1 choice
[309526.618534] usb 1-4.4: USB disconnect, address 21
[310306.836205] usb 1-4.4: new high speed USB device using ehci_hcd and address 22
[310306.930475] usb 1-4.4: configuration #1 chosen from 1 choice
$ 

```

---

### Post by katykat on 2010-10-24
I have this problem in Meerkat, as well. 

Everything mounts fine, but manually, from Nautilus.

---

### Post by stringarray on 2010-10-24
> **katykat said:**
> I have this problem in Meerkat, as well. 

Everything mounts fine, but manually, from Nautilus.

I can't even mount manually, help :)

---

