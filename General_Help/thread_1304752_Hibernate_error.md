---
title: "Hibernate error"
date: 2009-10-29
forum: General Help
---

### Post by Jamesss on 2009-10-29
For a long time now my computer has not been able to hibernate properly (I never needed to use it until now). After clicking hibernate from the shutdown options I get the following error messages:

```
Oct 29 18:00:37 james-desktop kernel: [  752.244383] suspend_device(): scsi_bus_suspend+0x0/0x70 returns -5
Oct 29 18:00:37 james-desktop kernel: [  752.244386] PM: Device 0:0:0:0 failed to freeze: error -5
```

From here I can't shutdown, resume, or do anything useful. I just do a hard reset with the power switch for four seconds.

Can anyone help?

---

### Post by Jamesss on 2009-11-30
So i still have this problem, even after a fresh install of Karmic. Whenever I try to hibernate, I get this error:

```
Nov 30 17:49:10 james-desktop kernel: [ 6080.319104] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.319139] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.319150] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.319151]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.319155] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.324218] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.324224] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.324231] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.324236] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.324249] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.324256] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.324257]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.324260] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.332204] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.332207] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.332212] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.332216] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.332228] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.332235] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.332236]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.332239] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.340202] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.340205] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.340210] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.340213] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.340225] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.340232] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.340234]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.340236] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.348202] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.348205] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.348209] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.348212] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.348225] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.348231] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.348233]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.348236] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.356201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.356204] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.356208] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.356212] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.356224] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6080.356231] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.356232]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.356235] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.364201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6080.364204] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.364212] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6080.364500] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6080.364517] ata1.01: limiting speed to UDMA/133:PIO6
Nov 30 17:49:10 james-desktop kernel: [ 6080.364521] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Nov 30 17:49:10 james-desktop kernel: [ 6080.364529] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6080.364530]          res 50/00:fe:00:00:00/00:00:00:00:00/f0 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6080.364533] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6080.364543] ata1: soft resetting link
Nov 30 17:49:10 james-desktop kernel: [ 6081.536203] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.536206] ata1.01: device reported invalid CHS sector 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.536210] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.536214] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.536226] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.536234] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.536235]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.536238] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.544202] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.544207] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.544210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.544222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.544229] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.544231]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.544234] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.552202] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.552206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.552210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.552222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.552229] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.552230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.552233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.560201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.560206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.560209] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.560221] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.560228] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.560230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.560233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.568201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.568206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.568209] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.568221] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.568228] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.568230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.568232] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.576201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.576208] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.576421] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.576436] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6081.576444] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.576445]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.576448] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.584204] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6081.584209] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6081.584212] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6081.584224] ata1.01: limiting speed to UDMA/33:PIO6
Nov 30 17:49:10 james-desktop kernel: [ 6081.584228] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Nov 30 17:49:10 james-desktop kernel: [ 6081.584235] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6081.584236]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6081.584239] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6081.584246] ata1: soft resetting link
Nov 30 17:49:10 james-desktop kernel: [ 6082.756201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6082.756206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6082.756210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6082.756222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6082.756229] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6082.756230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6082.756233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6082.764202] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6082.764207] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6082.764210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6082.764222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6082.764229] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6082.764230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6082.764233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6082.772201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6082.772206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6082.772210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6082.772222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6082.772228] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6082.772230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6082.772233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6082.780201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6082.780206] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6082.780210] it821x: can't process command 0xE7
Nov 30 17:49:10 james-desktop kernel: [ 6082.780222] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 30 17:49:10 james-desktop kernel: [ 6082.780228] ata1.01: cmd e7/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov 30 17:49:10 james-desktop kernel: [ 6082.780230]          res 50/00:01:01:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 30 17:49:10 james-desktop kernel: [ 6082.780233] ata1.01: status: { DRDY }
Nov 30 17:49:10 james-desktop kernel: [ 6082.788201] ata1.01: configured for DMA
Nov 30 17:49:10 james-desktop kernel: [ 6082.788208] ata1: EH complete
Nov 30 17:49:10 james-desktop kernel: [ 6082.788415] sd 0:0:1:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 30 17:49:10 james-desktop kernel: [ 6082.788420] sd 0:0:1:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Nov 30 17:49:10 james-desktop kernel: [ 6082.788425] sd 0:0:1:0: [sda] Add. Sense: No additional sense information
Nov 30 17:49:10 james-desktop kernel: [ 6082.788443] device_suspend(): scsi_bus_suspend+0x0/0x60 returns -5
Nov 30 17:49:10 james-desktop kernel: [ 6082.788446] PM: Device 0:0:1:0 failed to freeze: error -5
Nov 30 17:49:10 james-desktop kernel: [ 6082.788494] sd 2:0:0:0: [sdb] Starting disk
Nov 30 17:49:10 james-desktop kernel: [ 6082.800073] sd 2:0:1:0: [sdc] Starting disk
Nov 30 17:49:10 james-desktop kernel: [ 6082.952182] PM: Image restored successfully.
Nov 30 17:49:10 james-desktop kernel: [ 6082.960872] Restarting tasks ... done.
Nov 30 17:49:10 james-desktop kernel: [ 6082.961427] PM: Basic memory bitmaps freed
Nov 30 17:49:10 james-desktop kernel: [ 6083.728326] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Nov 30 17:49:20 james-desktop kernel: [ 6093.804009] eth0: no IPv6 routers present
```

So it seems that the ite8212 driver doesn't support the hibernate function, but I also get a similar message which breifly flashes up on the screen when I shut down. So the output of sudo lshw -C storage is:

```
  *-storage               
       description: RAID bus controller
       product: IT/ITE8212 Dual channel ATA RAID controller
       vendor: Integrated Technology Express, Inc.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: scsi0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: storage pm bus_master cap_list rom emulated
       configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8
       resources: irq:18 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) memory:dffe0000-dfffffff(prefetchable)
  *-ide
       description: IDE interface
       product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
       vendor: VIA Technologies, Inc.
       physical id: 11.1
       bus info: pci@0000:00:11.1
       logical name: scsi2
       logical name: scsi3
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_via latency=32
       resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)

```

So is this a problem with the driver=pata_it821x?

---

### Post by fluffman86 on 2009-11-30
With karmic, I've found that hibernation actually takes longer than shutting down and rebooting.  If you need karmic to remember what's running, you can have it always do so in System > Preferences > Startup Applications.

---

### Post by Jamesss on 2009-11-30
Thanks for the info but I really wanted to use hibernate or perhaps suspend so that I can wake my pc up with WOL over the internet. Is there a way to change the driver? I downloaded some ITE8212 drivers from their website and tried to use sudo insmod iteraid.o but I get:
```
insmod: error inserting 'iteraid.o': -1 Invalid module format
```

any other ideas?

---

