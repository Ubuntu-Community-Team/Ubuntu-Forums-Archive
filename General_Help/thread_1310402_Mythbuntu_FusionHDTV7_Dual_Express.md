---
title: "Mythbuntu FusionHDTV7 Dual Express"
date: 2009-11-01
forum: General Help
---

### Post by Yiftos on 2009-11-01
I have built a Mythbuntu 9.04 AMD64 with a Divco Dual Express FusionHDTV7 capture card. I downloaded and installed the both firmware versions for this card from Stevens site. If you see below the Dmesg list it seems top have been discovered with the 1.1 firmware loaded. However, When I load it on my backend server it lists as dvb card, Samsung S5H1411 QAM/8VSB. I tried to scan over the air channels but does not lock on any of the channels. I know the stations are within two miles and an outside antenna connected. The same one to my flat screen tv which works fine. I should not need Schedules.org just to lock on signals. 
Could this be a defective card or am I missing something.
 
Bytes.
[    9.718516] [fglrx]   vendor: 1002 device: 9614 count: 1
[    9.718660] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
[    9.718669] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.718671] pci 0000:01:05.0: setting latency timer to 64
[    9.720895] [fglrx] Driver built-in PAT support is enabled successfully
[    9.720922] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[    9.746883] Linux video capture interface: v2.00
[    9.774586] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.783062] cx23885 driver version 0.0.1 loaded
[    9.783086] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.783166] CORE cx23885[0]: subsystem: 18ac:d618, board: DViCO FusionHDTV7 Dual Express [card=10,autodetected]
[    9.830456] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.830485] HDA Intel 0000:01:05.1: setting latency timer to 64
[    9.949365] cx23885_dvb_register() allocating 1 frontend(s)
[    9.949367] cx23885[0]: cx23885 based dvb card
[   10.037038] xc5000 1-0064: creating new instance
[   10.037722] xc5000: Successfully identified at address 0x64
[   10.037723] xc5000: Firmware has not been loaded previously
[   10.037725] DVB: registering new adapter (cx23885[0])
[   10.037727] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   10.037919] cx23885_dvb_register() allocating 1 frontend(s)
[   10.037920] cx23885[0]: cx23885 based dvb card
[   10.083657] xc5000 2-0064: creating new instance
[   10.084340] xc5000: Successfully identified at address 0x64
[   10.084341] xc5000: Firmware has not been loaded previously
[   10.084342] DVB: registering new adapter (cx23885[0])
[   10.084343] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   10.084507] cx23885_dev_checkrevision() New hardware revision found 0x0
[   10.084509] cx23885_dev_checkrevision() Hardware revision unknown 0x0
[   10.084515] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfbc00000
[   10.084521] cx23885 0000:02:00.0: setting latency timer to 64
[   10.216658] lp: driver loaded but no devices found

[   21.249677] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   21.249679] i2c-adapter i2c-1: firmware: requesting dvb-fe-xc5000-1.1.fw
[   21.308405] xc5000: firmware read 12332 bytes.
[   21.308406] xc5000: firmware upload

---

### Post by Yiftos on 2009-11-05
I decided to upgrade Mythbuntu from 9.04 to 9.10. What a difference! Much more polished, better interface, compare/contrast to almost night and day. Within mesg 9.10 requested the latest firmware ([http://www.mythtv.org/wiki/Talk:DViCO_FusionHDTV7_Dual_Express](http://www.mythtv.org/wiki/Talk:DViCO_FusionHDTV7_Dual_Express)) for the Fusion card which I loaded. Now the FusionHDTV7 Dual Express is seen by my front end with most ATSC channels functioning. However, when trying to scan air waves it still states no lock on all the frequencies even thought MY Frontend displays the HD content. I noticed within my My frontend that the signal strength is only 2.4db 0% with an outside antenna while my external USB tuner with the outside antenna gets 30db 90% and 25-26db 80% with an 8" whip. Many towers are within 2-3 miles. I believe I have a defective card and not the firmware loaded. I am sending it back for a replacement. Will let you know what happens.:

---

