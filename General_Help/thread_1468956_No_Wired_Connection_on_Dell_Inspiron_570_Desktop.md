---
title: "No Wired Connection on Dell Inspiron 570 Desktop"
date: 2010-05-01
forum: General Help
---

### Post by Cerin on 2010-05-01
I just bought a basic Dell Inspiron 570 Desktop, and installed Ubuntu 9.10, and found that the wired internet won't connect. I've checked the wire, and confirmed that an Ubuntu laptop can get a wired connection using it, but the new Inspiron doesn't do anything.

The "Network Connections" dialog shows a "Wired connection 1" item, but Network Manager refuses to connect to it. ifconfig only shows the lo interface.

How can I get this wired interface working? Please, this is very frustrating. I can only assume it's some sort of driver issue (which seems rare with the wired connection), but I can't even run an update since I don't have an internet connection.

---

### Post by garvinrick4 on 2010-05-01
> **Cerin said:**
> I just bought a basic Dell Inspiron 570 Desktop, and installed Ubuntu 9.10, and found that the wired internet won't connect. I've checked the wire, and confirmed that an Ubuntu laptop can get a wired connection using it, but the new Inspiron doesn't do anything.

The "Network Connections" dialog shows a "Wired connection 1" item, but Network Manager refuses to connect to it. ifconfig only shows the lo interface.

How can I get this wired interface working? Please, this is very frustrating. I can only assume it's some sort of driver issue (which seems rare with the wired connection), but I can't even run an update since I don't have an internet connection.

For some reason in the last few days I find a lot of users have forgotten to right click on network icon and check that there wired or wireless is check marked enabled.

---

### Post by Cerin on 2010-05-01
That's not the issue. The "Enable Networking" checkbox is checked. The "Edit Connections" dialog shows no wired interfaces.

> **garvinrick4 said:**
> For some reason in the last few days I find a lot of users have forgotten to right click on network icon and check that there wired or wireless is check marked enabled.

---

### Post by Cerin on 2010-05-01
Furthermore, running "lshw" shows a "Netlink BCM57788 Gigabit Ethernet PCIe Broadcom device, which is listed under "network UNCLAIMED".

I'm I correct in assuming that means Ubuntu doesn't have a 64-bit driver for this device? Is there anyway to get support for it, especially when the computer has no internet?

---

### Post by garvinrick4 on 2010-05-01
If you run this command it shows no driver?

lspci -v | less 

id:network
                   description: Ethernet interface                 product: RTL8101E/RTL8102E  PCI Express Fast Ethernet controller                 vendor: Realtek  Semiconductor Co., Ltd.                 physical id: 0
                 bus info: pci@0000:03:00.0
                 logical name: eth0
                 version: 02                 serial: 00:26:9e:4d:62:62                 width: 64  bits                 clock: 33MHz                 capabilities: bus_master cap_list rom ethernet physical                  configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes                 resources: irq:27 ioport:2000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

---

### Post by Cerin on 2010-05-01
At the end of the output, I see this:

```
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
        Subsystem: Dell Device 043b
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

Is this is what you mean?

---

### Post by garvinrick4 on 2010-05-01
I was trying to see a driver version, if was there. 

See where my driver version is on mine.

---

### Post by Cerin on 2010-05-01
I finally gave up and decided to simply wipe it out and try 10.04. Sure enough, the network card works on a fresh install. Of course sounds doesn't work, but that's another story...

---

### Post by ankanaan on 2011-06-24
I have two of these Dell desktops, one at home one at work.  Both run 10.04.  

The one at work never had any problem, the one at home had a flaky ethernet connection.  After many ubuntu upgrades the connection is not flaky anymore, however, it still goes down if I unplug the cable, reset the modem, or anything to upset it, even disabling enabling the connection on the panel.

This is lspci -v at work:

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Dell Device 0438
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [60] Vendor Specific Information <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 43-6d-06-fe-ff-db-ba-a4
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3


root@carina:~# uname -a
Linux carina 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux


And here lspci -v at home:


03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Dell Device 0438
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [60] Vendor Specific Information <?>
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 8f-6a-06-fe-ff-db-ba-a4
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

root@eniac:~# uname -a
Linux eniac 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux


I have checked every cable, etc.  Also, when the machine is running windows I can unplug cables, reset router, etc, etc, and the network comes back to work everytime :-(

Any clues aprreciated

---

