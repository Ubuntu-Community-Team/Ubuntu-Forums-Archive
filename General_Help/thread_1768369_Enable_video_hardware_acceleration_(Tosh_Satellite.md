---
title: "Enable video hardware acceleration (Tosh Satellite)?"
date: 2011-05-26
forum: General Help
---

### Post by jimcpl on 2011-05-26
Hi,

I installed Ubuntu on my Toshiba Satellite (L455-S5975) awhile ago, and it's upgraded to 11.04:

cat /etc/issue shows:

Ubuntu 11.04 \n \l

I haven't used Ubuntu much, but I was wondering if hardware acceleration is enabled on this installation, and if not, is there a way to enable it?

lspci -vv shows:

[HTML]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if
 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device ff01
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at f2400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0100c  Data: 4199
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff01
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f2100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
[/HTML]

I've been searching and found some info about enabling "UXA" in xorg.conf, but there is no xorg.conf on the system.

I also found info that says that I have to run "X11 -configure" but I've tried going to single-user mode (editing grub at boot), but when I do that, it just boots to a completely black screen and the Caps Lock LED keeps blinking.

Can anyone tell me how to (1) check if hardware acceleration is enabled, and (2) if it's not, how to enable on this laptop?

Thanks,
Jim

---

