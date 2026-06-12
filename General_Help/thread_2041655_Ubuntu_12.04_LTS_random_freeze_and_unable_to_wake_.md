---
title: "Ubuntu 12.04 LTS random freeze and unable to wake from suspend"
date: 2012-08-13
forum: General Help
---

### Post by lucaraki on 2012-08-13
Just built my first computer. Currently using Ubuntu 12.04 LTS 64-bit, but system seems to have a couple of problems.

1) Sometimes "everything" freezes, or at least the image does. I tried keyboard and mouse don't respond. I end up having to reboot via power button.
2) After suspend, I wake up the computer with the power button. The display and the computer wake up (LEDs are on), but no image shows. I searched the forums and tried the two scripts  [here]("http://ubuntuforums.org/showthread.php?t=1978290"), but it didn't solve the issue. The first time I tried the keyboard shortcut Alt+F1 then Alt+F7, it worked. The second time, it froze after Alt+F1, showing a command prompt.

cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=1bd21f4a-5991-4c6f-b5ee-6de3fa298925 ro quiet splash radeon.audio=1 vt.handoff=7
```

lsmod
```
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
joydev                 17693  0 
hid_logitech_dj        18594  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
usbhid                 47199  1 hid_logitech_dj
snd_hwdep              13668  1 snd_hda_codec
hid                    99559  2 hid_logitech_dj,usbhid
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
dm_multipath           23230  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
snd                    78855  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
shpchp                 37277  0 
i915                  472941  3 
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
mei                    41616  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
dm_raid45              78155  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
e1000e                156693  0 
crc_itu_t              12707  1 firewire_core
xor                    12894  1 dm_raid45
dm_mirror              22203  1 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  4 dm_raid45,dm_mirror,dm_region_hash
```

lspci
```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: mei
	Kernel modules: mei
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation H67 Express Chipset Family LPC Controller [8086:1c4a] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel modules: iTCO_wdt
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA Controller [RAID mode] [8086:2822] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel modules: i2c-i801
01:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
	Kernel modules: shpchp
03:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: xhci_hcd
04:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403] (rev 01)
	Subsystem: Intel Corporation Device [8086:2001]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
```

wakeup
```
Device	S-state	  Status   Sysfs node
P0P1	  S4	*disabled  
P0P2	  S4	*disabled  
P0P3	  S4	*disabled  
P0P4	  S4	*disabled  
GBE	  S4	*enabled   pci:0000:00:19.0
BR20	  S3	*disabled  
EUSB	  S3	*enabled   pci:0000:00:1d.0
USBE	  S3	*enabled   pci:0000:00:1a.0
PEX0	  S4	*disabled  pci:0000:00:1c.0
BR21	  S4	*disabled  pci:0000:01:00.0
PEX1	  S4	*disabled  
PEX2	  S4	*disabled  
PEX3	  S4	*disabled  pci:0000:00:1c.3
PEX4	  S4	*disabled  pci:0000:00:1c.4
PEX5	  S4	*disabled  
PEX6	  S4	*disabled  
PEX7	  S4	*disabled  
PWRB	  S3	*enabled   
```

dmidecode
```
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: BLH6710H.86A.0076.2010.1115.1959
	Release Date: 11/15/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: DH67GD
	Version: AAG10206-205
	Serial Number: BTGD120002FU
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

```

My desktop:

cpu: [INDENT]Intel Core-i5[/INDENT]
motherboard: [INDENT]Intel DH67GD[/INDENT]
memory: [INDENT]8GB (2 x 4GB) DDR3 SDRAM DDR3 1600[/INDENT]
disk: [INDENT]Crucial M4 64GB SATA SSD[/INDENT]
[INDENT]2X SAMSUNG Spinpoint F3 1TB 7200 RPM SATA 3.0Gb/s[/INDENT]

Note:
[INDENT]Using integrated graphics, no graphics card.
I have not found a pattern to when it freezes.
I allocated 4Gb for swap.
Boot drive is the SSD.
I use USB keyboard/mouse from Logitech (unifying receiver)[/INDENT]

Appreciate any help!

---

### Post by GreatDanton on 2012-08-13
That reminds me on problem with my laptop. Maybe this will not work but it cost you nothing to try this: [http://ubuntuforums.org/showpost.php?p=11827265&postcount=8](http://ubuntuforums.org/showpost.php?p=11827265&postcount=8)

Try this and then report what happened. If that's not working instead of **quiet splash i915.modeset=1** type:
**quiet splash i915.nomodeset=1**

Hope this helps.

---

### Post by lucaraki on 2012-08-22
Thanks for the response, but neither option solved the issue.

---

### Post by fafabone on 2012-08-23
I have the same chipset, the same Os and the same problem..Can you post a step-by-step guide to install Intel drivers on Ubuntu 12.04. PLease Help me!!

---

### Post by not so there on 2012-08-24
I'm having this same sort of issue with waking up the computer.
I have used both the 3.2 and the 3.4 kernel and I still have the problem. (I updated since I was having lock ups in unity and it is now much less often). I also installed 12.10 alpha 3 and have the problem. I also disabled the USB3.0 in the bios. Using a ga-z68xp-ud3 motherboard with i5 and a ATI 6950 video card.

I used the script you linked as well as this one, maybe you will have better luck with it.
[http://ubuntuforums.org/showpost.php...49&postcount=6](http://ubuntuforums.org/showpost.php...49&postcount=6)

---

### Post by lucaraki on 2012-08-25
> **not so there said:**
> I'm having this same sort of issue with waking up the computer.
I have used both the 3.2 and the 3.4 kernel and I still have the problem. (I updated since I was having lock ups in unity and it is now much less often). I also installed 12.10 alpha 3 and have the problem. I also disabled the USB3.0 in the bios. Using a ga-z68xp-ud3 motherboard with i5 and a ATI 6950 video card.

I used the script you linked as well as this one, maybe you will have better luck with it.
[http://ubuntuforums.org/showpost.php...49&postcount=6](http://ubuntuforums.org/showpost.php...49&postcount=6)

The link didn't work. The url has "..." in it... maybe a copy-paste error?

---

### Post by lucaraki on 2012-08-25
> **fafabone said:**
> I have the same chipset, the same Os and the same problem..Can you post a step-by-step guide to install Intel drivers on Ubuntu 12.04. PLease Help me!!

I didn't install drivers either, and would appreciate a step-by-step guide as well. Anyone can help us out? I'm not even sure if there are drivers available... maybe that's the problem?

Fafabone, could we compare what's different and what isn't with our configuration? My hope is that it would point out where the problem is....
My desktop:
[INDENT]
cpu:  Intel Core-i5
motherboard:  Intel DH67GD
memory:  8GB (2 x 4GB) DDR3 SDRAM DDR3 1600
boot disk:  Crucial M4 64GB SATA SSD
additional disks:  2X SAMSUNG Spinpoint F3 1TB 7200 RPM SATA 3.0Gb/s
Graphics card:  No, integrated graphics
Swap:  4Gb
KM:  both USB from Logitech (unifying receiver)
[/INDENT]

---

