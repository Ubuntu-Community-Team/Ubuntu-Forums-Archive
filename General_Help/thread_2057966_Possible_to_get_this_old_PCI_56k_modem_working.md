---
title: "Possible to get this old PCI 56k modem working"
date: 2012-09-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-09-14
Is there a way to get this ancient PCI 56k modem working on linux?
This card does have audio but i don't care if that part works, my onboard audio should be better
i was able to find it on google with "conexant 90079"
[[IMG]http://i.imgur.com/3KNu5l.jpg[/IMG]]("http://i.imgur.com/3KNu5.jpg")Linked to high resolution copy (2672 x 1672) 2.8MB
i would like to try and use it with this software
[https://code.google.com/p/linux-caller-id/](https://code.google.com/p/linux-caller-id/)

---

### Post by Frogs Hair on 2012-09-14
I have an old 56k modem and Ubuntu reports is as being installed when I run lspci in the terminal but I don't know if it works.```
01:05.0 Communication controller: LSI Corporation 56k WinModem (rev 01)
```

---

### Post by pbrane on 2012-09-14
have you seen this?
[http://www.linuxant.com/drivers/riptide/index.php]("http://www.linuxant.com/drivers/riptide/index.php")

---

### Post by pqwoerituytrueiwoq on 2012-09-14
> **pbrane said:**
> have you seen this?
[http://www.linuxant.com/drivers/riptide/index.php](http://www.linuxant.com/drivers/riptide/index.php)
worst case scenario i can get audio on that old box i had that card in
but i don't need audio for this purpose just the  modem part
i did not see the card in my lspci output when i had it installed

---

### Post by Epodx64 on 2012-09-14
You need to download the GPPP Ubuntu doesn't ship with the dial-up programs any more

---

### Post by pqwoerituytrueiwoq on 2012-09-14
> **Epodx64 said:**
> You need to download the GPPP Ubuntu doesn't ship with the dial-up programs any more
thanks will try the chip when i get a chance to put it back in, busy day

---

### Post by pqwoerituytrueiwoq on 2012-09-19
i got a second modem now
```
02:08.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
    Subsystem: Risq Modular Systems, Inc. Device 4311
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at fdce0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
02:0a.0 Communication controller: LSI Corporation Lucent V.92 Data/Fax Modem
    Subsystem: LSI Corporation Lucent V.92 Data/Fax Modem
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 255
    Region 0: I/O ports at da00 [size=256]
    Capabilities: [f8] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
```

---

### Post by CJ_Hudson on 2012-10-19
Hi, I am trying to get working / diagnose my Conexant PCI data fax modem.
It stopped working a week ago in Windows 7 and now I want to know if it's broken properly or if Windows is malfunctioning.

---

### Post by pqwoerituytrueiwoq on 2012-10-19
> **MogBug said:**
> Hi, I am trying to get working / diagnose my Conexant PCI data fax modem.
It stopped working a week ago in Windows 7 and now I want to know if it's broken properly or if Windows is malfunctioning.
does it show up in [FONT=Courier New]lspci[/FONT]? if not make sure it is seated properly and or try a different PCI slot, if it still does not shot up in lspci the card is probably dead

---

### Post by CJ_Hudson on 2012-11-25
Thanks pqwoerituytrueiwoq, I took the card out, rebooted, shut down, put the card back in, rebooted and everything was fine. Oh and I think Windows updated in between taking the card out and putting it back in again!
All fine and dandy now though.

---

### Post by dcstar on 2012-11-25
(Deleted)

---

