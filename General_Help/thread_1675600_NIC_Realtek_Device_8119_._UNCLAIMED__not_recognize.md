---
title: "NIC: Realtek Device 8119 . UNCLAIMED / not recognized / no driver?"
date: 2011-01-25
forum: General Help
---

### Post by Drostin77 on 2011-01-25
I cannot get Ubuntu to recognize my NIC.  The NIC is a realtek "Device 8119" (apparently).

Based on the thread here: [http://www.uluga.ubuntuforums.org/showthread.php?t=304208](http://www.uluga.ubuntuforums.org/showthread.php?t=304208)
I suspect it ought to work with the 8139too driver.  However sudo modprobe 8139too does not help, nor does placing 8139too in /etc/modules and rebooting (and unlike the poster in that thread I do not have a second working NIC lying around...)

This card was working under my Arch Linux install with all the same hardware previous to installing Ubuntu.  However I (stupidly) did not think to save that install anywhere and do not recall how I set it up.  I know I was not using ndiswrapper (though I would not mind using it now).  I suspect the 8139too driver should work, but is there any way for me to say "This device should use this driver, even if things might explode!"? (I'd rather troubleshoot exploding drivers than flail blindly trying to make my NIC get recognized).

I also found some information here (Japanese): [http://joezn.blog93.fc2.com/category2-0.html](http://joezn.blog93.fc2.com/category2-0.html)
Seems to indicate that sometimes the driver for 8119 will load in ubuntu 10.10, possibly only if 8169 driver is installed.

Googling for Realtek 8119 is pretty fruitless.  I can certainly go pick up a cheap network card, but it seems a shame to waste working hardware.

I have tried to put the output of commands I saw requested in other NIC related threads below.  I forgot to get one (no longer at troubled machine): ifconfig -a.  It is only showing loopback.

Below are: "lshw -C Network" "lspci -v -v" "lsmod" and "dmesg | grep eth", all run as root.

**lspci -v -v (relevant section only)**
```
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Device 8119 (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8119
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0 (16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at ec00 [size=256]
	Region 1: Memory at fda00000 (32-bit, non-prefetchable) [disabled] [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

```

**lshw -C network**
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=64
       resources: ioport:ec00(size=256) memory:fda00000-fda000ff 
```

**lsmod**
```
Module                  Size  Used by
binfmt_misc             6599  1 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   218227  1 
snd_hda_intel          22107  2 
fglrx                2269685  96 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ppdev                   5556  0 
parport_pc             26058  1 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i82975x_edac            2551  0 
soundcore                880  1 snd
psmouse                59033  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  1 fglrx
edac_core              38630  1 i82975x_edac
led_class               2633  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
firewire_ohci          21042  0 
hid                    67742  1 usbhid
floppy                 54311  0 
ahci                   19198  0 
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
libahci                21664  1 ahci
pata_jmicron            1855  0 
```

[B]dmesg | grep eth (nothing to see here, heh)
[/B]
```
[    0.176000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PDC] (Node f7022408), AE_ALREADY_EXISTS
[    0.176000] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
```

[EDIT1]

In the following pdf about an x86 real time operating system...(I CANNOT VOUCH FOR THIS PDF BEING SAFE!!!) : [http://www.intervalzero.com/pdfs/Network_Drivers_Supported_in_ETS.pdf](http://www.intervalzero.com/pdfs/Network_Drivers_Supported_in_ETS.pdf)
I found the following lines: 
Device ID | Device Description
0x8139    | RTL-8139/8139C/8139C+, Realtek RTL8139 Family PCI Fast Ethernet NIC
0x8169    | RTL8119, Single Gigabit LOM Ethernet Controller

Which Has led me to the (very poorly formed bordering an arbitrary) theory that the 8119 is somehow the same as the 8169! and as such the 8169 driver should work! This theory is untested and not very well thought out.  Will test it out tonight (Japan time)

---

### Post by Drostin77 on 2011-01-27
Thanks to this post, from google translate of a German forum:

"Yeaaaaaaah it, I finally made it. the problem was probably the main board ... if the map NEN now bissel slipped in slot, then it is not recognized correctly. after thousands expandable orgies I then just the map a little differently than before purely screwed, and now it is recognized again as before, perfectly"
([http://translate.google.com/translate?hl=en&sl=de&u=http://www.hardwareluxx.de/community/f211/probleme-nach-umbau-linux-242679.html&ei=p5c_TZewIJHCvQOYr5jBAw&sa=X&oi=translate&ct=result&resnum=1&ved=0CBoQ7gEwAA&prev=/search%3Fq%3D%2522Device%2B8119%2B(rev%2B10)%2522%2Br8169%26hl%3Den%26client%3Dfirefox-a%26hs%3DFOc%26rls%3Dorg.mozilla:en-US:official%26prmd%3Divns](http://translate.google.com/translate?hl=en&sl=de&u=http://www.hardwareluxx.de/community/f211/probleme-nach-umbau-linux-242679.html&ei=p5c_TZewIJHCvQOYr5jBAw&sa=X&oi=translate&ct=result&resnum=1&ved=0CBoQ7gEwAA&prev=/search%3Fq%3D%2522Device%2B8119%2B(rev%2B10)%2522%2Br8169%26hl%3Den%26client%3Dfirefox-a%26hs%3DFOc%26rls%3Dorg.mozilla:en-US:official%26prmd%3Divns))

I figured out that I needed to re-seat the card.  Now its recognized as a 8139 card and works perfectly.  Not sure what exactly google translate was going for but... i got the gist?

---

