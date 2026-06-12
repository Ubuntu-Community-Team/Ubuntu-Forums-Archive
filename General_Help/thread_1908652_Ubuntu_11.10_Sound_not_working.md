---
title: "Ubuntu 11.10 Sound not working"
date: 2012-01-13
forum: General Help
---

### Post by triunenature on 2012-01-13
Just upgraded to ubuntu 11.10

When I login the login sound is very choppy.

Whenever I play music the sound is also choppy.  However if I go to sound settings --> hardware --> "Test", it sounds fine.

The choppy sound is for both online and local files.  Doesn't happen in windows, didn't happen in ubuntu 11.04

lscpi -v:
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fb000000-fcffffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 42
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a58
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

01:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device c959
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at f9f80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nvidia_173, nouveau, nvidiafb

03:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel modules: shpchp

04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs SB1040
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fddfc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

lsmod
```

Module                  Size  Used by
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rc_winfast             12454  0 
tuner_simple           18151  1 
tuner_types            18998  1 tuner_simple
nvidia              10390874  40 
snd_hda_codec_ca0110    13209  1 
snd_usb_audio         100880  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_ca0110,snd_hda_intel
snd_pcm                80468  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_timer              28932  2 snd_seq,snd_pcm
snd_rawmidi            25241  2 snd_seq_midi,snd_usbmidi_lib
snd_seq_device         14172  3 snd_seq_midi,snd_seq,snd_rawmidi
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
gspca_sn9c20x          35334  0 
psmouse                73673  0 
gspca_main             27610  1 gspca_sn9c20x
snd                    55902  17 snd_seq,snd_hda_codec_ca0110,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_timer,snd_rawmidi,snd_seq_device
tuner                  26836  2 
k8temp                 12905  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
binfmt_misc            17292  1 
ir_rc5_decoder         12490  0 
cx8800                 33328  0 
ir_nec_decoder         12490  0 
cx88xx                 78930  1 cx8800
rc_core                25797  9 rc_winfast,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  5 gspca_main,tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
shpchp                 32356  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sata_nv                23379  2 
forcedeth              58103  0 
pata_amd               13753  0 

```

---

### Post by triunenature on 2012-01-14
So I know bumping isn't good...

But just as an FYI, my USB headset works just fine, just my soundcard.

I really would like to use my speakers:D

---

### Post by holycow131415 on 2012-01-14
Do you use VLC player? Maybe you should download it from software center and use that to play media. It comes with codecs and such. To me it sounds like a codec problem.

---

### Post by triunenature on 2012-01-15
> **holycow131415 said:**
> Do you use VLC player? Maybe you should download it from software center and use that to play media. It comes with codecs and such. To me it sounds like a codec problem.

Yes, i do use VLC, however the default login sound should play no matter what media player you have, and it doesn't play correctly.  Also VLC doesn't handle youtube, and youtube videos (rather sound from the videos) is choppy as well.

It sounds like a driver issue, but I know not how to fix it.

Also like mentioned before, when I use my usb headset, it works fine (since its not using my soundcard).  Which proves that media player/codecs arn't the issue.

---

