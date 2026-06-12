---
title: "WiFi driver"
date: 2011-02-13
forum: General Help
---

### Post by DeMus on 2011-02-13
Hi,
Does anybody know of a Linux driver for a wireless networkcard with a RTL8192CU chip?
I own a Hercules Pico Stick USB WiFi N150 802.11n and until now I can not find a working driver? Who has the same chip and a working network connection?

---

### Post by gandaran on 2011-02-13
check this if it helps
[http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/](http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/)

---

### Post by DeMus on 2011-02-13
> **gandaran said:**
> check this if it helps
[http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/](http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/)

Thank you very much for your answer. However, I don't have the RTL8192SU but the RTL8192CU.
Doing it the way you showed me didn't work for me unfortunately. Do you have any other ideas?.
Thanks again.

---

### Post by walt.smith1960 on 2011-02-13
Have you looked in the Networking & wireless forums, and perhaps do a search? There are a few threads in that forum which may provide some help.   Wireless networking issues seem to be the most common in Ubuntu but most can be solved with some perseverance.

---

### Post by gandaran on 2011-02-13
post the output of 
```
dmesg | grep 819
```
maybe you should post in the networking and wireless section, you will get better and quicker support there or search there.

---

### Post by DeMus on 2011-02-13
> **gandaran said:**
> post the output of 
```
dmesg | grep 819
```
maybe you should post in the networking and wireless section, you will get better and quicker support there or search there.

Thank you guys. I will have a look in the network and wireless section. I always come here because I think this section is the most active one.
I did what you asked me and this is the result:

```
dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.728819] pci 0000:00:1c.5:   IO window: 0x2000-0x2fff
[    0.819793] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.819895] usb usb2: configuration #1 chosen from 1 choice
[    0.819919] hub 2-0:1.0: USB hub found
[    0.819925] hub 2-0:1.0: 6 ports detected
[    0.819974] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.819990] uhci_hcd: USB Universal Host Controller Interface driver
[    1.281934] ata2.00: ATA-7: Hitachi HDT725050VLA380, V56OA7EA, max UDMA/133
[    1.281937] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.819660] Initializing USB Mass Storage driver...
[    1.822494] ata7: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
[    1.822497] ata8: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe180 irq 16
[    2.181902] atl1 0000:02:00.0: version 2.1.3
```

is this any good because I have no idea what I am looking at. Sorry.
Thanks again for your help, without guys like you I would be returning to the dark side of the software I guess. (Sorry, just saw a StarWars movie)

---

