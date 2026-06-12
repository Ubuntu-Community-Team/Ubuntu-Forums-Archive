---
title: "Problem with HPLIP and PCI parallel port"
date: 2010-12-20
forum: General Help
---

### Post by hilbert00 on 2010-12-20
Dear friend,

  I've bought a brand new computer as a Xmas present for my father and I managed to convince him to give Ubuntu a try. I managed to make him 90% happy and the unhappiness comes from the fact he isn't able to print with his beloved HP OfficeJet Pro 1150C. 

The situation is rather complicated. The printer has only a Parallel port connection but the pc came w/o such ports. I've added a PCI parallel port card and connected the printer but with no (or very little) luck. 

I think the problem is with the card and not with the printer because of the following considerations.

After a fresh reboot, I give the command lspci -vv and I get the following:

```

03:05.0 Parallel controller: Timedia Technology Co Ltd SUN1888 (Dual IEEE1284 parallel port) (rev 01) (prog-if 02 [ECP])
    Subsystem: Timedia Technology Co Ltd PAR4008A
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 20
    Region 0: I/O ports at e000 [size=8]
    Region 1: I/O ports at e008 [size=8]
    Kernel driver in use: parport_pc
    Kernel modules: parport_pc

```

This seems to prove that the card is recognised and installed. Right?

Then I run the hp-check and it finds my printer but only for a second, because if I repeat hp-check or I send any other command to the printer I receive a communication error. At this point, if I redo an lspci -vv the output is different! 

```


03:05.0 Parallel controller: Timedia Technology Co Ltd SUN1888 (Dual IEEE1284 parallel port) (rev 01) (prog-if 02 [ECP])
    Subsystem: Timedia Technology Co Ltd PAR4008A
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 20
    Region 0: I/O ports at e000 **[disabled]** [size=8]
    Region 1: I/O ports at e008 **[disabled] **[size=8]
    Kernel driver in use: parport_pc
    Kernel modules: parport_pc


```Note that they are disabled! And the card will stay disabled until the next reboot. 

Is there anything special I need to do to configure the pci card? Do you have any further advice?

Thanks a lot for every help! 

cheers,
hilbert

---

