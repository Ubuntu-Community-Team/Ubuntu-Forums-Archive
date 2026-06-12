---
title: "Using setpci to change interrupts on PCI-X devices"
date: 2011-04-29
forum: General Help
---

### Post by kb7qdi on 2011-04-29
I am running Ubuntu Server 10.04 LTS on a HP ML110 G6 (Dual-core 1.86Ghz, 2 Gig RAM).

I have one Digium TE121 T1 PCI-X and one Digium AEX800 8 port FXS card.  Server is running Asterisk version 1.6.

I am getting hissing and static sounds on some calls.  I am also getting IRQ conflicts every once in a great while.  One of the possible causes of this is because all three cards share the same IRQ (16).  IRQ 16 is also being shared by the USB drivers, but I'm not using any at this time.

Digium made a couple recommendations.  First was to turn ACPI on.  I did that, and I can verify that it's on, but the IRQ settings remains the same.

The other recommendation by Digium is to use setpci to allocate an IRQ for each card.  I am unfamiliar with setpci.  I have tried using setpci to confirm that I am at least in the right direction by trying to find the value that relates to IRQ 16.  At least if I have that I might be able to change the value.

However, from the list of acceptable parameters to view (used the Ubuntu man page web site for 10.04 LTS), none of the values come back as either the hex, binary or decimal value of 16.

I would appreciate any suggestions.

Dean Hoover
Milwaukee, Wisconsin

--------------

root@asterisk-fl:~# lspci -vvvxxx -s 02:08.0
02:08.0 Ethernet controller: Digium, Inc. Wildcard TE121 single-span T1/E1/J1 card (PCI-Express) (rev 11)
        Subsystem: Digium, Inc. Wildcard TE121 single-span T1/E1/J1 card (PCI-Express)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (16000ns min, 32000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 2000 [size=256]
        Region 1: Memory at df900000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: wcte12xp
        Kernel modules: wcte12xp
00: 61 d1 00 80 57 01 90 02 11 00 00 02 08 20 00 00
10: 01 20 00 00 00 00 90 df 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 61 d1 00 80
30: 00 00 00 00 c0 00 00 00 00 00 00 00 05 01 40 80
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 17 13 81 09 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 01 00 02 7e 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

--------------

---

