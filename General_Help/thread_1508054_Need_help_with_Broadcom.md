---
title: "Need help with Broadcom"
date: 2010-06-12
forum: General Help
---

### Post by m623d on 2010-06-12
I have tried ubuntu for the past few years, I have a Pavilion DV9000 laptop and most things worked out of the box, but it wasnt developed enough for me to switch permanently from M$ which is/was my goal.
Then along come 9.0 and then, wow, 10. Excellent OS, was starting to use more and more, when suddenly I get an update (10.04 I think) and bang, Wifi doesnt work anymore :(
tried all the 'fixes' on here, but no joy.
Why has Ubuntu taken a step back?
I'm at the point of giving up to be honest.
I know M$ is paid for, but everything just works out of the box, and any problems are Sooooo easy to fix.
Linux is too techy, I dont want to have to 'fix' it every week to make it work, let alone delve into DOS type commands from the eighties.
Granted Linux has come along way, and I really thought Ubuntu 10 was the 'switch' I was waiting for.
SO disappointed.

Anyone know of an easy fix for the Broadcom wifi on my laptop?
Ubuntu 10.04 64 bit
Please reinstate my passion for linux

---

### Post by 3Miro on 2010-06-12
Are you looking for help or ranting?

Most likely the wifi driver did not register with the new version of the kernel. Try uninstalling and reinstalling the driver from System -> Admin -> Hardware Drivers.

If that doesn't work, hold down the shift key when booting and select one of the "older" versions of the kernel (try third from the top).

The only reason why Windows works out of the box is because you got someone else (the manufacturer) to install it for you (and the wifi manufacturer doesn't give a free driver for Linux).

The Terminal is not from the 80's it is just more advanced and you get advice involving typing simply because it is easier than long explanations on how to navigate between piles of menus.

Have you tried to fix something that doesn't work "out of the box" under windows. It is just as techy as Linux, if not more so. The main issue of fixing problems with windows comes from the fact that unlike Linux windows is not transparent at all.

---

### Post by elliotn on 2010-06-12
My ubuntu 10.04 is working fine, faster than windows 7, and it got looks too. A step back? Well its your opinion.

---

### Post by gingivere0 on 2010-06-12
Since Wi-fi isn't working, hook your computer up to the internet via an ethernet cable.  Then go System>Administration>Hardware Drivers and pick one to install.  Then restart and it should be working.

---

### Post by jnorthr on 2010-06-12
you can peek at the log files by going to system>admin>view log files, then look at the bottom of the panel for the latest messages. it will give us some clues as to what needs to be fixed.

---

### Post by oxf on 2010-06-12
> **m623d said:**
> I have tried ubuntu for the past few years, I have a Pavilion DV9000 laptop and most things worked out of the box, but it wasnt developed enough for me to switch permanently from M$ which is/was my goal.
Then along come 9.0 and then, wow, 10. Excellent OS, was starting to use more and more, when suddenly I get an update (10.04 I think) and bang, Wifi doesnt work anymore :(
tried all the 'fixes' on here, but no joy.
Why has Ubuntu taken a step back?
I'm at the point of giving up to be honest.
I know M$ is paid for, but everything just works out of the box, and any problems are Sooooo easy to fix.
Linux is too techy, I dont want to have to 'fix' it every week to make it work, let alone delve into DOS type commands from the eighties.
Granted Linux has come along way, and I really thought Ubuntu 10 was the 'switch' I was waiting for.
SO disappointed.


Anyone know of an easy fix for the Broadcom wifi on my laptop?
Ubuntu 10.04 64 bit
Please reinstate my passion for linux

The BC43XX wifi card can be a bit problomatic. But.... I've got it working every time and now I almost do it with my eyes closed. You need Ndiswrapper an BCfwcutter and should be fine

---

### Post by dim3000 on 2010-06-12
> **m623d said:**
> I have tried ubuntu for the past few years, I have a Pavilion DV9000 laptop and most things worked out of the box, but it wasnt developed enough for me to switch permanently from M$ which is/was my goal.
Then along come 9.0 and then, wow, 10. Excellent OS, was starting to use more and more, when suddenly I get an update (10.04 I think) and bang, Wifi doesnt work anymore :(
tried all the 'fixes' on here, but no joy.
Why has Ubuntu taken a step back?
I'm at the point of giving up to be honest.
I know M$ is paid for, but everything just works out of the box, and any problems are Sooooo easy to fix.
Linux is too techy, I dont want to have to 'fix' it every week to make it work, let alone delve into DOS type commands from the eighties.
Granted Linux has come along way, and I really thought Ubuntu 10 was the 'switch' I was waiting for.
SO disappointed.

Anyone know of an easy fix for the Broadcom wifi on my laptop?
Ubuntu 10.04 64 bit
Please reinstate my passion for linux

I had a dv9000 (sold recently) everything works great, just install the drivers from Hardware Drivers.

---

### Post by SlidingHorn on 2010-06-12
for your wireless issue, please see the link in my signature and post those outputs.  Can't help if we don't know what you're using

---

### Post by m623d on 2010-06-12
Was kinda a shout for help, not a rant.
Was a bit fed up this afty after spending all day trying to fix this.
I do like Ubuntu 10 and desperatly want it to work for me, and all was going well until the update!
Anyway, I've run the commands and pasted results below.
Hope someone can help!


HP Pavilion DV9655ea
```

mark@Ubuntu-Laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```
```

mark@Ubuntu-Laptop:~$ lsusb
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

mark@Ubuntu-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c1:bf:1a  
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fec1:bf1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1235281 (1.2 MB)  TX bytes:258137 (258.1 KB)
          Interrupt:20 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:b2:e8:2c  
          inet6 addr: fe80::21a:73ff:feb2:e82c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:148
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
```

mark@Ubuntu-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:167
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
```

mark@Ubuntu-Laptop:~$ lsmod
Module                  Size  Used by
xt_limit                2180  8 
xt_tcpudp               2667  7 
ipt_LOG                 5370  8 
ipt_MASQUERADE          1863  0 
xt_DSCP                 2277  0 
ipt_REJECT              2384  1 
nf_conntrack_irc        4429  0 
nf_conntrack_ftp        7126  0 
xt_state                1490  6 
nls_utf8                1421  1 
udf                    85529  1 
crc_itu_t               1715  1 udf
joydev                 11072  0 
binfmt_misc             7960  1 
snd_hda_codec_conexant    28745  1 
ppdev                   6375  0 
iptable_nat             5219  0 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  9 iptable_nat,nf_nat
nf_conntrack           73934  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  0 
iptable_filter          2791  1 
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22429  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
lib80211_crypt_tkip     8676  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70978  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ricoh_mmc               3416  0 
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  1 sdhci
psmouse                64608  0 
serio_raw               4918  0 
k8temp                  3912  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
nvidia              10799466  41 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
ahci                   37646  2 
forcedeth              55592  0 
pata_amd               11962  1 

```
```

[    0.334623] pci 0000:07:05.2: PME# disabled
[    0.334649] pci 0000:07:05.3: reg 10 32bit mmio: [0xf2101000-0xf21010ff]
[    0.334682] pci 0000:07:05.3: supports D1 D2
[    0.334684] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334688] pci 0000:07:05.3: PME# disabled
[    0.334715] pci 0000:07:05.4: reg 10 32bit mmio: [0xf2101400-0xf21014ff]
[    0.334747] pci 0000:07:05.4: supports D1 D2
[    0.334749] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.334753] pci 0000:07:05.4: PME# disabled
[    0.334787] pci 0000:00:08.0: transparent bridge
[    0.334791] pci 0000:00:08.0: bridge 32bit mmio: [0xf2100000-0xf21fffff]
[    0.334876] pci 0000:03:00.0: reg 10 64bit mmio: [0xf2000000-0xf2003fff]
[    0.334887] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xf2500000-0xf25fffff]
[    0.334925] pci 0000:03:00.0: supports D1 D2
[    0.334976] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf20fffff]
[    0.334980] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf2500000-0xf25fffff]
[    0.335026] pci 0000:05:00.0: reg 10 32bit mmio: [0xce000000-0xceffffff]
[    0.335039] pci 0000:05:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.335053] pci 0000:05:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]
[    0.335061] pci 0000:05:00.0: reg 24 io port: [0x4000-0x407f]
[    0.335070] pci 0000:05:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.335151] pci 0000:00:0d.0: bridge io port: [0x4000-0x4fff]
[    0.335154] pci 0000:00:0d.0: bridge 32bit mmio: [0xcc000000-0xceffffff]
[    0.335158] pci 0000:00:0d.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.335197] pci 0000:00:0e.0: bridge io port: [0x5000-0x5fff]
[    0.335200] pci 0000:00:0e.0: bridge 32bit mmio: [0xf0000000-0xf1ffffff]
[    0.335204] pci 0000:00:0e.0: bridge 64bit mmio pref: [0xf2600000-0xf27fffff]
[    0.335218] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.335305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.335350] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.335394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.335427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.335468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[    0.362813] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *15
[    0.363024] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *10
[    0.363234] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.363445] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.363653] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[    0.363861] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.364072] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.364283] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *15
[    0.364491] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.364699] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.364914] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7
[    0.365126] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.365334] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *11
[    0.365546] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.365765] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.365974] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *0, disabled.
[    0.366111] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.366114] vgaarb: loaded
[    0.366252] SCSI subsystem initialized
[    0.366386] libata version 3.00 loaded.
[    0.366466] usbcore: registered new interface driver usbfs
[    0.366479] usbcore: registered new interface driver hub
[    0.366509] usbcore: registered new device driver usb
[    0.366710] ACPI: WMI: Mapper loaded
[    0.366712] PCI: Using ACPI for IRQ routing
[    0.366900] NetLabel: Initializing
[    0.366902] NetLabel:  domain hash size = 128
[    0.366903] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.366919] NetLabel:  unlabeled traffic allowed by default
[    0.366964] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.366969] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.380004] Switching to clocksource hpet
[    0.382049] AppArmor: AppArmor Filesystem Enabled
[    0.382073] pnp: PnP ACPI init
[    0.382094] ACPI: bus type pnp registered
[    0.383362] ACPI Error: Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) (20090903/dsopcode-596)
[    0.383370] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node ffff8800bc6399c0), AE_AML_BUFFER_LIMIT
[    0.383410] ACPI Error (uteval-0250): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node ffff8800bc6399c0), AE_AML_BUFFER_LIMIT
[    0.383419] pnp 00:03: can't evaluate _CRS: 12298
[    0.385182] pnp: PnP ACPI: found 12 devices
[    0.385185] ACPI: ACPI bus type pnp unregistered
[    0.385198] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.385207] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.385210] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.385218] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.385221] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.385225] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.385228] system 00:0b: iomem range 0xfec80000-0xfec80fff has been reserved
[    0.385231] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.389994] pci 0000:00:08.0: PCI bridge, secondary bus 0000:07
[    0.389997] pci 0000:00:08.0:   IO window: disabled
[    0.390001] pci 0000:00:08.0:   MEM window: 0xf2100000-0xf21fffff
[    0.390012] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.390017] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01
[    0.390019] pci 0000:00:0b.0:   IO window: disabled
[    0.390022] pci 0000:00:0b.0:   MEM window: disabled
[    0.390024] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.390028] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.390030] pci 0000:00:0c.0:   IO window: disabled
[    0.390033] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf20fffff
[    0.390037] pci 0000:00:0c.0:   PREFETCH window: 0x000000f2500000-0x000000f25fffff
[    0.390043] pci 0000:05:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.390046] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:05
[    0.390049] pci 0000:00:0d.0:   IO window: 0x4000-0x4fff
[    0.390052] pci 0000:00:0d.0:   MEM window: 0xcc000000-0xceffffff
[    0.390055] pci 0000:00:0d.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.390059] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:09
[    0.390062] pci 0000:00:0e.0:   IO window: 0x5000-0x5fff
[    0.390065] pci 0000:00:0e.0:   MEM window: 0xf0000000-0xf1ffffff
[    0.390068] pci 0000:00:0e.0:   PREFETCH window: 0x000000f2600000-0x000000f27fffff
[    0.390078] pci 0000:00:08.0: setting latency timer to 64
[    0.390084] pci 0000:00:0b.0: setting latency timer to 64
[    0.390089] pci 0000:00:0c.0: setting latency timer to 64
[    0.390094] pci 0000:00:0d.0: setting latency timer to 64
[    0.390099] pci 0000:00:0e.0: setting latency timer to 64
[    0.390103] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.390105] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.390109] pci_bus 0000:07: resource 1 mem: [0xf2100000-0xf21fffff]
[    0.390111] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.390114] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.390117] pci_bus 0000:03: resource 1 mem: [0xf2000000-0xf20fffff]
[    0.390120] pci_bus 0000:03: resource 2 pref mem [0xf2500000-0xf25fffff]
[    0.390123] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
[    0.390126] pci_bus 0000:05: resource 1 mem: [0xcc000000-0xceffffff]
[    0.390128] pci_bus 0000:05: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.390131] pci_bus 0000:09: resource 0 io:  [0x5000-0x5fff]
[    0.390134] pci_bus 0000:09: resource 1 mem: [0xf0000000-0xf1ffffff]
[    0.390137] pci_bus 0000:09: resource 2 pref mem [0xf2600000-0xf27fffff]
[    0.390183] NET: Registered protocol family 2
[    0.390393] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.392499] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.399421] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.400338] TCP: Hash tables configured (established 524288 bind 65536)
[    0.400341] TCP reno registered
[    0.400458] NET: Registered protocol family 1
[    0.400605] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400656] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400723] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400788] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400856] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400930] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.400964] pci 0000:05:00.0: Boot video device
[    0.401174] Simple Boot Flag at 0x36 set to 0x1
[    0.401400] Scanning for low memory corruption every 60 seconds
[    0.401590] audit: initializing netlink socket (disabled)
[    0.401602] type=2000 audit(1276381270.389:1): initialized
[    0.411164] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.412694] VFS: Disk quotas dquot_6.5.2
[    0.412757] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.413448] fuse init (API version 7.13)
[    0.413549] msgmni has been set to 6020
[    0.413823] alg: No test for stdrng (krng)
[    0.413889] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.413892] io scheduler noop registered
[    0.413894] io scheduler anticipatory registered
[    0.413896] io scheduler deadline registered
[    0.413933] io scheduler cfq registered (default)
[    0.414124]   alloc irq_desc for 24 on node 0
[    0.414127]   alloc kstat_irqs on node 0
[    0.414136] pcieport 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.414142] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.414253]   alloc irq_desc for 25 on node 0
[    0.414255]   alloc kstat_irqs on node 0
[    0.414260] pcieport 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.414265] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.414371]   alloc irq_desc for 26 on node 0
[    0.414373]   alloc kstat_irqs on node 0
[    0.414378] pcieport 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.414383] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.414485]   alloc irq_desc for 27 on node 0
[    0.414487]   alloc kstat_irqs on node 0
[    0.414492] pcieport 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.414497] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.414564] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.414592] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.415199] ACPI: AC Adapter [ACAD] (on-line)
[    0.415297] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.415573] ACPI: Lid Switch [LID]
[    0.415641] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.415645] ACPI: Power Button [PWRB]
[    0.415693] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.415696] ACPI: Sleep Button [SLPB]
[    0.415748] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.415751] ACPI: Power Button [PWRF]
[    0.416147] ACPI: processor limited to max C-state 1
[    0.416178] processor LNXCPU:00: registered as cooling_device0
[    0.416386] processor LNXCPU:01: registered as cooling_device1
[    0.420078] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)
[    0.421934] Linux agpgart interface v0.103
[    0.421976] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.423250] brd: module loaded
[    0.423731] loop: module loaded
[    0.423852] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.424222] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.424944] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    0.424950]   alloc irq_desc for 23 on node 0
[    0.424953]   alloc kstat_irqs on node 0
[    0.424964] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[    0.424995] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    0.425004] pata_acpi 0000:00:0a.0: PCI INT A disabled
[    0.440428] Fixed MDIO Bus: probed
[    0.440468] PPP generic driver version 2.4.2
[    0.440534] tun: Universal TUN/TAP device driver, 1.6
[    0.440536] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.440633] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.450468] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17
[    0.450475]   alloc irq_desc for 17 on node 0
[    0.450477]   alloc kstat_irqs on node 0
[    0.450488] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17
[    0.450511] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.450515] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.450612] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.450649] ehci_hcd 0000:00:02.1: debug port 1
[    0.450657] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.450681] ehci_hcd 0000:00:02.1: irq 17, io mem 0xf2488000
[    0.470229] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.470392] usb usb1: configuration #1 chosen from 1 choice
[    0.470433] hub 1-0:1.0: USB hub found
[    0.470444] hub 1-0:1.0: 10 ports detected
[    0.470532] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.480682] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.480689]   alloc irq_desc for 18 on node 0
[    0.480692]   alloc kstat_irqs on node 0
[    0.480703] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.480729] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.480732] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.480819] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.480857] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf2486000
[    0.532182] usb usb2: configuration #1 chosen from 1 choice
[    0.532230] hub 2-0:1.0: USB hub found
[    0.532243] hub 2-0:1.0: 10 ports detected
[    0.532324] uhci_hcd: USB Universal Host Controller Interface driver
[    0.532409] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.537723] Freeing initrd memory: 8135k freed
[    0.554307] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.554314] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.554429] mice: PS/2 mouse device common for all mice
[    0.554600] rtc_cmos 00:07: RTC can wake from S4
[    0.554651] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.554689] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.554828] device-mapper: uevent: version 1.0.3
[    0.554939] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.555018] device-mapper: multipath: version 1.1.0 loaded
[    0.555021] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.555194] cpuidle: using governor ladder
[    0.555196] cpuidle: using governor menu
[    0.555598] TCP cubic registered
[    0.555731] NET: Registered protocol family 10
[    0.556249] lo: Disabled Privacy Extensions
[    0.556550] NET: Registered protocol family 17
[    0.556593] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    0.556646] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x13
[    0.556648] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[    0.556651] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[    0.556654] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    0.556856] PM: Resume from disk failed.
[    0.556879] registered taskstats version 1
[    0.557249]   Magic number: 14:59:401
[    0.557356] rtc_cmos 00:07: setting system clock to 2010-06-12 22:21:11 UTC (1276381271)
[    0.557360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.557362] EDD information not available.
[    0.575122] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.680395] ACPI: Battery Slot [BAT0] (battery present)
[    0.780032] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.930410] Freeing unused kernel memory: 876k freed
[    0.930920] Write protecting the kernel read-only data: 7680k
[    0.940694] usb 1-4: configuration #1 chosen from 1 choice
[    0.954459] udev: starting version 151
[    1.125259] pata_amd 0000:00:09.0: version 0.4.1
[    1.125308] pata_amd 0000:00:09.0: setting latency timer to 64
[    1.126226] scsi0 : pata_amd
[    1.128701] scsi1 : pata_amd
[    1.129503] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    1.129506] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    1.129628] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.130266] ohci1394 0000:07:05.0: enabling device (0100 -> 0102)
[    1.130367] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.130375]   alloc irq_desc for 20 on node 0
[    1.130377]   alloc kstat_irqs on node 0
[    1.130388] forcedeth 0000:00:06.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.130393] forcedeth 0000:00:06.0: setting latency timer to 64
[    1.131590] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.131600] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.192054] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f2100000-f21007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.300354] ata1.00: ATAPI: PIONEER DVDRW   DVR-K17B, 1.02, max MWDMA2
[    1.300382] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.340037] usb 2-6: new low speed USB device using ohci_hcd and address 2
[    1.340303] ata1.00: configured for MWDMA2
[    1.346962] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW   DVR-K17B 1.02 PQ: 0 ANSI: 5
[    1.349274] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.349277] Uniform CD-ROM driver Revision: 3.20
[    1.349399] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.349465] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.349555] ata2: port disabled. ignoring.
[    1.568167] usb 2-6: configuration #1 chosen from 1 choice
[    1.582724] usbcore: registered new interface driver hiddev
[    1.588392] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-6/2-6:1.0/input/input6
[    1.588506] generic-usb 0003:046D:C03D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-6/input0
[    1.588540] usbcore: registered new interface driver usbhid
[    1.588543] usbhid: v2.6:USB HID core driver
[    1.651201] forcedeth 0000:00:06.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:c1:bf:1a
[    1.651207] forcedeth 0000:00:06.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.651475] ahci 0000:00:0a.0: version 3.0
[    1.651489] ahci 0000:00:0a.0: PCI INT A -> Link[LTID] -> GSI 23 (level, low) -> IRQ 23
[    1.651584] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.651589] ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led clo pmp pio ccc 
[    1.651593] ahci 0000:00:0a.0: setting latency timer to 64
[    1.652031] scsi2 : ahci
[    1.652165] scsi3 : ahci
[    1.652245] scsi4 : ahci
[    1.652323] scsi5 : ahci
[    1.652489] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.652492] ata4: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.652495] ata5: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484200 irq 23
[    1.652499] ata6: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484280 irq 23
[    2.000040] ata5: SATA link down (SStatus 0 SControl 300)
[    2.000053] ata6: SATA link down (SStatus 0 SControl 300)
[    2.510315] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00f90b7700]
[    2.580033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.580046] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.580414] ata3.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
[    2.580417] ata3.00: 312581808 sectors, multi 16: LBA48 
[    2.580428] ata4.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
[    2.580432] ata4.00: 312581808 sectors, multi 16: LBA48 
[    2.580884] ata3.00: configured for UDMA/100
[    2.580914] ata4.00: configured for UDMA/100
[    2.600151] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
[    2.600355] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.600472] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
[    2.600479] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.600608] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.600634] sd 2:0:0:0: [sda] Write Protect is off
[    2.600637] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.600689] sd 3:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.600695] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.600750] sd 3:0:0:0: [sdb] Write Protect is off
[    2.600753] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.600779] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.600897]  sda:
[    2.600983]  sdb: sda1 sda2
[    2.642403] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.651820]  sdb1 sdb2 sdb3 sdb4 < sdb5 >
[    2.688605] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.931631] kjournald starting.  Commit interval 5 seconds
[    2.931644] EXT3-fs: mounted filesystem with ordered data mode.
[   19.333992] udev: starting version 151
[   19.347746] Adding 4095992k swap on /dev/sdb3.  Priority:-1 extents:1 across:4095992k 
[   19.383305] lp: driver loaded but no devices found
[   19.420216] EXT3 FS on sdb2, internal journal
[   19.640841] acpi device:26: registered as cooling_device2
[   19.641021] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:24/LNXVIDEO:01/input/input7
[   19.641085] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.644142] vga16fb: initializing
[   19.644148] vga16fb: mapped to 0xffff8800000a0000
[   19.644218] fb0: VGA16 VGA frame buffer device
[   19.842806] type=1505 audit(1276377690.782:2):  operation="profile_load" pid=706 name="/sbin/dhclient3"
[   19.843106] type=1505 audit(1276377690.782:3):  operation="profile_load" pid=706 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.843279] type=1505 audit(1276377690.782:4):  operation="profile_load" pid=706 name="/usr/lib/connman/scripts/dhclient-script"
[   19.881629] nvidia: module license 'NVIDIA' taints kernel.
[   19.881634] Disabling lock debugging due to kernel taint
[   20.044139] eth0: no link during initialization.
[   20.047953] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.314966] lib80211: common routines for IEEE802.11 drivers
[   20.314970] lib80211_crypt: registered algorithm 'NULL'
[   20.335036] EDAC MC: Ver: 2.1.0 Jun  3 2010
[   20.342651] sdhci: Secure Digital Host Controller Interface driver
[   20.342655] sdhci: Copyright(c) Pierre Ossman
[   20.348242] Linux video capture interface: v2.00
[   20.352424] ricoh-mmc: Ricoh MMC Controller disabling driver
[   20.352427] ricoh-mmc: Copyright(c) Philip Langdale
[   20.494184] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   20.506598] input: HP Webcam as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input8
[   20.506661] usbcore: registered new interface driver uvcvideo
[   20.506664] USB Video Class driver (v0.1.0)
[   20.568691] nvidia 0000:05:00.0: power state changed by ACPI to D0
[   20.569050] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   20.569055]   alloc irq_desc for 19 on node 0
[   20.569057]   alloc kstat_irqs on node 0
[   20.569069] nvidia 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   20.569076] nvidia 0000:05:00.0: setting latency timer to 64
[   20.569082] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.569441] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   20.574498] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   20.574602] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   20.577145] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[   20.577151]   alloc irq_desc for 16 on node 0
[   20.577153]   alloc kstat_irqs on node 0
[   20.577165] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   20.577171] wl 0000:03:00.0: setting latency timer to 64
[   20.587677] EDAC amd64_edac:  Ver: 3.2.0 Jun  3 2010
[   20.592548] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 22)
[   20.592999] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   20.593013] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   20.595203] Registered led device: mmc0::
[   20.596323] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   20.598048] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   20.605217] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 12)
[   20.605237] ricoh-mmc: Controller is now disabled.
[   20.662725] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   20.663313] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   20.663315]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   20.663317]  (Note that use of the override may cause unknown side effects.)
[   20.665396] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   20.668956] lib80211_crypt: registered algorithm 'TKIP'
[   20.669190] eth1: Broadcom BCM4328 802.11 Hybrid Wireless Controller 5.60.48.36 
[   20.670860] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   20.670866]   alloc irq_desc for 21 on node 0
[   20.670868]   alloc kstat_irqs on node 0
[   20.670880] HDA Intel 0000:00:07.0: PCI INT B -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   20.670883] hda_intel: Disable MSI for Nvidia chipset
[   20.670928] HDA Intel 0000:00:07.0: setting latency timer to 64
[   20.671017] Console: switching to colour frame buffer device 80x30
[   20.746789] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.787074] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.789054] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   20.789059] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   20.789061] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.905252] type=1505 audit(1276377691.842:5):  operation="profile_load" pid=1023 name="/usr/share/gdm/guest-session/Xsession"
[   20.907334] type=1505 audit(1276377691.842:6):  operation="profile_replace" pid=1024 name="/sbin/dhclient3"
[   20.907637] type=1505 audit(1276377691.842:7):  operation="profile_replace" pid=1024 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.907810] type=1505 audit(1276377691.842:8):  operation="profile_replace" pid=1024 name="/usr/lib/connman/scripts/dhclient-script"
[   20.913509] type=1505 audit(1276377691.852:9):  operation="profile_load" pid=1025 name="/usr/bin/evince"
[   20.917702] type=1505 audit(1276377691.852:10):  operation="profile_load" pid=1025 name="/usr/bin/evince-previewer"
[   20.920219] type=1505 audit(1276377691.862:11):  operation="profile_load" pid=1025 name="/usr/bin/evince-thumbnailer"
[   21.300332] ppdev: user-space parallel port driver
[   21.548558] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   21.624078] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   31.410025] eth1: no IPv6 routers present
[   83.010046] Clocksource tsc unstable (delta = -302933212 ns)
[  273.880575] UDF-fs: Partition marked readonly; forcing readonly mount
[  273.946812] UDF-fs INFO UDF: Mounting volume 'CNC3', timestamp 2007/03/07 04:35 (103c)
[  322.630008] eth0: link up.
[  322.632226] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  332.752510] eth0: no IPv6 routers present
[  716.210553] CE: hpet increasing min_delta_ns to 15000 nsec

```
```

mark@Ubuntu-Laptop:~$ sudo lshw -C network
[sudo] password for mark: 
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:c1:bf:1a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.88 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:b2:e8:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff(prefetchable)

```
```

mark@Ubuntu-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

mark@Ubuntu-Laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

mark@Ubuntu-Laptop:~$ uname -mr
2.6.32-22-generic x86_64

mark@Ubuntu-Laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


```
Thanks

---

### Post by SlidingHorn on 2010-06-12
No offense taken; it can be frustrating when things don't work the way you want.  We all understand :)  First, a possibly stupid question.  If you go to Menu > System > Hardware Drivers, is there a proprietary driver available for your wireless card?  If so, enable it and let me know if that works

---

### Post by linuxman94 on 2010-06-12
See this wiki page, it may help.

[Boadcom BCM43xx series]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#No%20Internet%20Access")

---

### Post by libssd on 2010-06-12
> **m623d said:**
> I have tried ubuntu for the past few years, I have a Pavilion DV9000 laptop and most things worked out of the box, but it wasnt developed enough for me to switch permanently from M$ which is/was my goal.
Then along come 9.0 and then, wow, 10. Excellent OS, was starting to use more and more, when suddenly I get an update (10.04 I think) and bang, Wifi doesnt work anymore :(
tried all the 'fixes' on here, but no joy.
Why has Ubuntu taken a step back?
I'm at the point of giving up to be honest.
I know M$ is paid for, but everything just works out of the box, and any problems are Sooooo easy to fix.
Linux is too techy, I dont want to have to 'fix' it every week to make it work, let alone delve into DOS type commands from the eighties.
Granted Linux has come along way, and I really thought Ubuntu 10 was the 'switch' I was waiting for.
SO disappointed.

Anyone know of an easy fix for the Broadcom wifi on my laptop?
Ubuntu 10.04 64 bit
Please reinstate my passion for linux
What version of Ubuntu were you running before 10.04? If it worked, why upgrade?

---

### Post by m623d on 2010-06-13
It lists the STA Broadcom (if I remember correctly) in the hardware drivers, and it says its activated.
I have tried disabling and re activating, but no joy.
I have a button on my lappy to turn wifi on and off, blue when on, orange when off. It is blue. I have also toggled  this switch as recommended, but still no wifi.

I was running 9, but did a clean install to 10.
I upgraded because Ubuntu seemed to be getting better and better and 10 (in my opinion) is a vast improvement.

Thanks

---

### Post by Metrop021 on 2010-06-13
This is a new release of ubuntu, so there's gonna be bugs and kinks to be worked out, if it really bugs you that much. use 9.10 and upgrade to 10.04 in a couple months or so and it should be fine

---

### Post by wilee-nilee on 2010-06-13
If you put that text read out in code tags it will be easier to read, and may motivate help.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Just hit the edit button and put one at the beginning one at the end.

---

### Post by m623d on 2010-06-13
Dont know what your talking about fella,
code this code that.
I did what was requested and pasted it

---

### Post by wilee-nilee on 2010-06-13
> **m623d said:**
> Dont know what your talking about fella,
code this code that.
I did what was requested and pasted it

Alright just trying to help, good luck.;)

---

### Post by m623d on 2010-06-13
tried what linuxman suggested from that wiki page, auto installed fwcutter.
no joy

can anybody help me?

---

### Post by benmoran on 2010-06-13
Have you tried un-installing and re-installing the driver under System-Administration-Hardware Drivers?

If you can't get it to work over the net, i'm sure you have a local Linux users group that can help you get it working. Broadcom drivers suck. I know since I've got one too. It's a shame since most other wireless chipset manufacturers release their specs, and they all work fine.

---

### Post by m623d on 2010-06-13
If yo mean deactivating then re activating, then yes, tried that

not looking good is it

---

### Post by issachan on 2010-06-13
> **m623d said:**
> I have tried ubuntu for the past few years, I have a Pavilion DV9000 laptop and most things worked out of the box, but it wasnt developed enough for me to switch permanently from M$ which is/was my goal.
Then along come 9.0 and then, wow, 10. Excellent OS, was starting to use more and more, when suddenly I get an update (10.04 I think) and bang, Wifi doesnt work anymore :(
tried all the 'fixes' on here, but no joy.
Why has Ubuntu taken a step back?
I'm at the point of giving up to be honest.
I know M$ is paid for, but everything just works out of the box, and any problems are Sooooo easy to fix.
Linux is too techy, I dont want to have to 'fix' it every week to make it work, let alone delve into DOS type commands from the eighties.
Granted Linux has come along way, and I really thought Ubuntu 10 was the 'switch' I was waiting for.
SO disappointed.

Anyone know of an easy fix for the Broadcom wifi on my laptop?
Ubuntu 10.04 64 bit
Please reinstate my passion for linux

I love Ubuntu! It's the best os in my opinion, and because it's free and  it's constantly a work in progress (but what isn't) I expect there to  be a few glitches and problems, but it's a lot better than fighting with  the numerous problems I've had with Microsoft's operating systems. It's also super easy and you don't have to be a programmer to type in a few commands every now and then. And as far as updates are concerned, what os (or even software in general) doesn't? 

**FYI - _A clean install works best_ - upgrading caused a lot  of things to not work properly on my computer. :)**

To get Ubuntu 10.04 to work properly on my system I ended up reinstalling it a  few times.  ](*,)

*(One of those reinstalls was because I tried to use Wine to install  Photoshop and it totally screwed up my system to the point where it took  over 4 or 5 minutes to boot up and the screen kept flickering and going  crazy. Anyway I won't be making that mistake again. My system does not  like the Wine program in general - it screws up everything every single  time I try to use it! Maybe it's because my system hates Windows and  anything that has to do with it..... sorry I'm rambling...*)

Anyway without Wine, my system usually boots up super fast and works  just like it's supposed to, I even got my canon printer working with a  little work when in the previous versions of Ubuntu, I couldn't. I think  it's generally a matter of figuring out the settings and talking with  those who encounter the same problems so as to work out a solution. 

While every now and then I end up waiting for what seems like forever  for the system to boot up due to some anomaly after downloading and  installing something and the occasional weird things that display while  booting, it's nothing compared to paying ridiculous sums to Microsoft :evil:  for their truly disappointing products which have monopolized the market. 

I think the Ubuntu community is doing an awesome job =D> and I'm thankful for the great people out there who have helped me in the past and those that will help me overcome problems in the future. 

And in regards to wifi issues.. if it's a driver issue maybe an international driver might work, which is the case for some printer drivers... it's probably an easy fix. Personally I hate trying to use wireless internet since I've never had any real success with it, thus I use a pretty blue ethernet cable but I also use a desktop computer, thus no need for mobility.

Don't give up on Ubuntu! The solution is out there! :KS

---

### Post by switch10 on 2010-06-13
Within the the past 10 years there have been what, 3 major OS releases from Windows?  Ubuntu has a new release every 6 months.  You by no means should feel like you have to upgrade with every new release.

Someone mentioned earlier in this post to hold shift when your computer is booting to get to the grub menu so you can go back to an earlier kernel.  

Try again when 10.10 is released.  If you really feel upgrading.

---

### Post by praveenthivari on 2010-06-13
Hi, I am not an expert in this and I dont hv aany wi-fi connection. But I would recommend u to uninstall the driver and then clean all configs related to it. Use ubuntu tweak or Ubuntu tools softwares. Even then just find out if any folder related to it left out, then try to reinstall the driver. For tht u may hv to connect it to wired network( I know it is stupid of tell this). Best of luck wid tht.

In my experience,  I hv not been able to get banshee itself work, after I installed lots of extra stuff. I could not figure out wat the prob was. In d end I reinstalled whole sys. Now apparently, everything works alright. I dont know wen I'll face another UNKNOWN prob.:-)

---

### Post by m623d on 2010-06-14
Any chance of getting back on track and helping me??

---

### Post by philinux on 2010-06-14
A few posts removed. Keep this on topic thanks.

---

### Post by CoolJohnB on 2010-06-14
I have a Dell Vostro 1700 and had the same problem, I just went to System Administration and Hardware Drivers, where 2 Broadcom drivers came up on the list after installing those everything worked fine, much prefer Ubuntu 10.04 to Windows 7 especially like the intuitiveness of it.

---

### Post by m623d on 2010-06-15
mine worked fine on 10.04 until it did a kernal update (I think)
tried loading previous one, but it dont work either now.

So is there no Linux master out there who can help?
I pasted the commands and responses earlier as requested, but still waiting for help.

i thought you came here for help???

---

### Post by Jake007g on 2010-06-15
> **m623d said:**
> mine worked fine on 10.04 until it did a kernal update (I think)
tried loading previous one, but it dont work either now.

So is there no Linux master out there who can help?
I pasted the commands and responses earlier as requested, but still waiting for help.

i thought you came here for help???

Plug in an alternative source of internet, like an ethernet for example.

Try ALT+F2, and typing
```
update-manager
```

See if there are any updates available. There may be kernel updates and many more important updates that you need if you've just installed a clean copy of Lucid. Install all the updates available, and let them do their thing which may take around 30 minutes if you haven't done any updates since the clean install.

Then reboot, and try re-installing your restricted broadcom wireless driver(s).

-Jake

---

### Post by m623d on 2010-06-15
Tried that.
Updated at same time as kernal update.
tried uninstalling driver then reinstall, no joy

---

### Post by amr mohsen on 2010-06-15
thanks alot

---

### Post by amr mohsen on 2010-06-15
how can i play fifa 200x on ubuntu):P

---

### Post by m623d on 2010-06-17
Woo Hoo! finally sorted.

In desperation I installed Opensuse 11.2 over my ubuntu, but OMG how I prefer Ubuntu. To be fair its probably because I used the KDE desktop for the first time. Anyway, same issues with wifi and Nvida graphic driver was a pain too. (even more command line stuff)
I stuck with it for a couple of days, but wasnt getting anywhere, and seemed to have more issues than ubuntu.
So this afty I have formatted and done a complete reinstall of Ubuntu 10.04
and after a couple of updates/reboots, all drivers where in place and, yep you guessed it, WIFI WORKS! 

So now I'll continue with my quest to not rely on M$ anymore.
easier said than done, as there are a few programs I need, but hopefully you kind people will help me find alternatives

I'll post a list soon of all the things I need

Thanks

M

---

