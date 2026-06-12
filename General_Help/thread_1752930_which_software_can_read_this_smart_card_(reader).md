---
title: "which software can read this smart card (reader)?"
date: 2011-05-08
forum: General Help
---

### Post by sanderj on 2011-05-08
Hi,

I've got a laptop with a smart card reader, and a compatible smart card (a company access card).

Keywords:O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller, yenta_cardbus

Which Ubuntu software can I use to read the smart card?
And can I use this card reader to read smart cards for TV-signals, for example in combination with CCcam?

Thanks.


Relevant output of lspci -vvv :

```
08:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
	Subsystem: Fujitsu Limited. Device 131e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0203000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 4c000000-4ffff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
	Subsystem: Fujitsu Limited. Device 131e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f0204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=0d, subordinate=10, sec-latency=176
	Memory window 0: 44000000-47fff000 (prefetchable)
	Memory window 1: 50000000-53fff000
	I/O window 0: 00005800-000058ff
	I/O window 1: 00005c00-00005cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
```


Stuff with 'card' from dmesg:
```

sander@lifebook:~$ dmesg | grep -i card
[    0.285411] pci 0000:08:03.0: CardBus bridge to [bus 09-0c]
[    0.285443] pci 0000:08:03.1: CardBus bridge to [bus 0d-10]
[    0.542460] isapnp: Scanning for PnP cards...
[    0.571787] EISA: Detected 0 cards.
[   21.490878] yenta_cardbus 0000:08:03.0: CardBus bridge found [10cf:131e]
[   21.490906] yenta_cardbus 0000:08:03.0: O2: enabling read prefetch/write burst
[   21.618058] yenta_cardbus 0000:08:03.0: ISA IRQ mask 0x0c38, PCI irq 16
[   21.618064] yenta_cardbus 0000:08:03.0: Socket status: 30000006
[   21.618082] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   21.627144] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [mem 0xf0200000-0xf02fffff]
[   21.627171] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
[   21.705240] yenta_cardbus 0000:08:03.1: CardBus bridge found [10cf:131e]
[   21.855578] yenta_cardbus 0000:08:03.1: ISA IRQ mask 0x0c38, PCI irq 16
[   21.855583] yenta_cardbus 0000:08:03.1: Socket status: 30000410
[   21.855599] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   21.862353] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [mem 0xf0200000-0xf02fffff]
[   21.862381] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [mem 0x40000000-0x47ffffff pref]
[   22.752117] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
sander@lifebook:~$ 

```

Something I tried (don't know if it makes sense):

```

sander@lifebook:~$ sudo pcscd -f -d
00000000 debuglog.c:230:DebugLogSetLevel() debug level=debug
01020484 pcscdaemon.c:512:main() pcsc-lite 1.5.5 daemon ready.
00377439 hotplug_libusb.c:403:HPEstablishUSBNotifications() Driver ifd-ccid.bundle does not support IFD_GENERATE_HOTPLUG. Using active polling instead.
00000048 hotplug_libusb.c:412:HPEstablishUSBNotifications() Polling forced every 1 second(s)


```

After "sudo apt-get install coolkey pcscd pcsc-tools", I get little result with pcsc_scan:


```
sander@lifebook:~$ sudo pcsc_scan
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
Waiting for the first reader...

```

and

```

sander@lifebook:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="O2Micro"
PRODID_2="SmartCardBus Reader"
PRODID_3="V1.0"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255
sander@lifebook:~$ pccardctl status
Socket 0:
  no card
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) [unbound]
sander@lifebook:~$
```

... all with the smartcard inserted (but apparently not detected?)

---

### Post by sanderj on 2011-05-08
I tried gscriptor, but no result. See screendumps.

---

