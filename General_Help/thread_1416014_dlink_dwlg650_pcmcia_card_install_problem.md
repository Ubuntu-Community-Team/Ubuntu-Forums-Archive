---
title: "dlink dwlg650 pcmcia card install problem"
date: 2010-02-25
forum: General Help
---

### Post by lomar72 on 2010-02-25
Hi I'm new to Xumbuntu, I have an older Toshiba laptop, Satellite pro 4600, 650 celeron,   Everything seems to get setup correctly except for the wireless card. I've been going through all the searches on here found quite a few of them helpfull, but stillhave not gotten the card working. I unistalled Network manager, installed wicd, this let me setup the card and got the lights blinking on it, It finds the network, and shows connection, but still cannot access the internet, or able to download files. I'ved tried madwiki drivers, windows drivers, atheros drivers, I was using 9.10 ad then tried 9.04 cause I read others had the same problem when switching to the newer version. here is what lspci -vv calls it.  I'm learing lots about liniux and having fun, but I'm missing something,  I appriciate any help, thanks
Bob

03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: D-Link System Inc Device 3202
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 2c000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath_pci, ath5k

---

