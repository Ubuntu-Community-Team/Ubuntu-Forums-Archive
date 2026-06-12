---
title: "limited screen resolution ubuntu 11.04"
date: 2011-07-25
forum: General Help
---

### Post by Detroit_Bad_Boy on 2011-07-25
I just acquired an acer AL1912 19" LCD monitor. The native resolution is higher than what ubuntu offers. I can't get above 1024 x 768. Is there an update that will allow for better resolution settings? Really need to know as it is causing a sparkly pixelization in certain areas of graphics.

---

### Post by 23dornot23d on 2011-07-25
What computer do you use and what graphics card does it use ?

> 
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
    Subsystem: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Region 1: Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>


Found it in one of your earlier posts .... if its the same .... if its intel I will let someone else deal with it ......

---

### Post by Detroit_Bad_Boy on 2011-07-25
> **23dornot23d said:**
> What computer do you use and what graphics card does it use ?


It's an Acer power desktop PC with onboard video. what command do I use in a terminal to get exact specs?

---

### Post by 23dornot23d on 2011-07-25
**lspci -v **

Will give more information ....

---

