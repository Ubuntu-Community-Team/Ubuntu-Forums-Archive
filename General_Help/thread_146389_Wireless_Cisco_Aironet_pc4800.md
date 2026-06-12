---
title: "Wireless Cisco Aironet pc4800"
date: 2006-03-18
forum: General Help
---

### Post by copycon on 2006-03-18
Wireless Cisco Aironet pc4800

I can not get this card up and running.  I do not know what the problem is everyother distro I have used with this card it always works right out of the box.  When I run:
Control Center>Internet & Network>Network Settings
I then click the administrator mode button and it shows Eth0 configured with DHCP and if I have a network cable plugged in it will show the IP address and that it is active.  It also shows an Eth1 disabled wireless network device and Wifi0 disabled wireless device.  If I click on the configure button the process crashes everytime.

Here is the output I get from the following commands:
menders1@mobile1:~$ sudo cardctl info
PRODID_1="Aironet"
PRODID_2="PC4800"
PRODID_3=""
PRODID_4=""
MANFID=015f,0007
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

menders1@mobile1:~$ sudo cardctl ident
Socket 0:
  product info: "Aironet", "PC4800"
  manfid: 0x015f, 0x0007
  function: 6 (network)
Socket 1:
  no product info available

menders1@mobile1:~$ sudo lspci -v
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f4200000-f5ffffff

0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM: Unknown device 0130
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-103ff000 (prefetchable)
        Memory window 1: 10400000-107ff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
        Subsystem: IBM: Unknown device 0130
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 10800000-10bff000 (prefetchable)
        Memory window 1: 10c00000-10fff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
        Subsystem: Intel Corp. EtherExpress PRO/100+ MiniPCI
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at f4120000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1800 [size=64]
        Memory at f4100000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [dc] Power Management version 2

0000:00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem (prog-if 02 [16550])
        Subsystem: Intel Corp.: Unknown device 2408
        Flags: medium devsel, IRQ 11
        I/O ports at 1840 [size=8]
        Memory at f4121000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM: Unknown device 0153
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at f4122000 (32-bit, non-prefetchable) [size=4K]
        Memory at f4000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2

0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1850 [size=16]

0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 1860 [size=32]

0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad A20m
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=256]
        Memory at f4200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] AGP version 1.0
        Capabilities: [5c] Power Management version 2

TIA for any help you could provide

---

### Post by copycon on 2006-03-19
Bump back to front

---

