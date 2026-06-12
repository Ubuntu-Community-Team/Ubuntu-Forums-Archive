---
title: "x86_64 no usb"
date: 2009-12-03
forum: General Help
---

### Post by johenkel on 2009-12-03
This is a Compaq Presario SR1817CL, AMD Athlon64 3200+.
I installed 9.10 on it and all the usb does not work.

Here are some error messages:
dmesg:
[    5.882048] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    5.882055] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.092073] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    6.092144] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.302053] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    6.302113] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.512132] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    6.512192] hub 1-0:1.0: hub_port_status failed (err = -32)
[    6.722059] ehci_hcd 0000:00:13.2: port 7 reset error -110
[    6.722120] hub 1-0:1.0: hub_port_status failed (err = -32)

when I do "lsusb" it shows :
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So some usb IS there but if I stick anything into a usb socket, nothing happens.
Somewhere I had read about loading ehci_hcd before uhci_hcd, but that was for a Fedora system and I have no idea how I tell ubuntu using one usb module before another one.

I hope anybody can help !!!!
*fingertwist*

johenkel

---

