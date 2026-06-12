---
title: "Unity 3D/wireless problems on HP laptop (12.04)"
date: 2012-04-30
forum: General Help
---

### Post by JayWalker256 on 2012-04-30
So my laptop is an HP DV6227CL. It's about 6 years old, and I used to run 10.04 (64-bit) on it with 0 problems, everything worked great out of the box. This has not been the case with Ubuntu 12.04 (64-bit). Not sure if I should split these into different threads but here's some of the problems I've been having.

1. After installing Nvidia-current (or even post-release) drivers, Unity 3D + compiz crashes on login, and goes to a black screen. 

2. Wifi doesn't work. The "hardware-drivers" app detects and installs drivers for my Broadcom wireless chip (Broadcom STA wireless driver), but once rebooted the networking applet does not show wireless connections, and the light on my wireless on/off switch always stays off.

There are numerous other little issues, but these are the biggest ones for me. If someone can point me in the right direction to fixing, that would be appreciated.

Here's the output of lspci:

```

00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: NVIDIA Corporation MCP51 PMU (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: NVIDIA Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

and lsmod:

```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
dm_crypt               23125  1 
bnep                   18281  2 
rfcomm                 47604  0 
nvidia              12319264  33 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_conexant    62128  1 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
parport_pc             32866  0 
snd_hwdep              13668  1 snd_hda_codec
ppdev                  17113  0 
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
wl                   2568210  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
joydev                 17693  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
nv_tco                 13687  0 
nand_ids               12723  1 nand
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    33087  2 sm_common,nand
r592                   18144  0 
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
soundcore              15091  1 snd
k8temp                 13057  0 
psmouse                87692  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
serio_raw              13211  0 
memstick               16569  1 r592
nand_ecc               13230  1 nand
lib80211               14381  1 wl
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
edac_core              53746  0 
mac_hid                13253  0 
edac_mce_amd           23709  0 
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
firewire_ohci          41000  0 
sdhci_pci              18826  0 
firewire_core          63558  1 firewire_ohci
uas                    18027  0 
usb_storage            49198  0 
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
forcedeth              63460  0 
pata_amd               14118  0 
sata_nv                32286  2 
video                  19596  0 

```

---

