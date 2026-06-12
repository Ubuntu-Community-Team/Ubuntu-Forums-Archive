---
title: "How to change screen resolution?"
date: 2011-12-05
forum: General Help
---

### Post by soreyes on 2011-12-05
Hi everyone,

Could anyone walk me step by step on how to change my screen resolution? When I go into System Settings, it only offers me two resolutions to choose from, neither of which is suitable. The resolution I have now is 1024x768. It is way too low. My eyes are hurting and I'm getting a headache from looking at the screen. As you can probably tell, I"m new to all this. Thanks for any help.

---

### Post by satanselbow on 2011-12-05
Not a lot of info to go on... you might need drivers that are not installed out of the box.

What is the output of 

```
lspci | grep 'VGA'

```


and 

```
xrandr
```

---

### Post by soreyes on 2011-12-05
Thanks for your reply. The outputs I get are:

```
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file


```and

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

```

---

### Post by soreyes on 2011-12-08
*bump*

---

### Post by dandnsmith on 2011-12-08
We still don't really have anything to go on.
What you've posted shows that you're at the upper limit of the driver(s) you have in use.

In order to get rather better info please do:
*sudo lspci -v*
and post the sections showing the graphics controller  - there are probably two of them, one of which will be showing the kernel module(s) in use.

You could go further, and examine the results of *sudo lsmod* to pull out the driver modules which refer to that particular module for us to consider.

---

### Post by soreyes on 2011-12-08
Ok, this is what I get:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Intel Corporation 4 Series Chipset DRAM Controller
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 810a
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at feaf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80200000-803fffff
    Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Biostar Microtech Int'l Corp Device 3103
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Biostar Microtech Int'l Corp Device 3103
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at feaf7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: [50] Subsystem: Biostar Microtech Int'l Corp Device 3103

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Biostar Microtech Int'l Corp Device 5202
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: medium devsel, IRQ 5
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Biostar Microtech Int'l Corp Device 2801
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-dc-73-fa-00-30-67-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

``````

Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_via      61329  1 
ppdev                  12849  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
atl1c                  36638  0 

```

---

### Post by dandnsmith on 2011-12-09
Right - so the relevant chipset stuff is
```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Biostar Microtech Int'l Corp Device 3103
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

```
and the modules bits
```
i915                  505108  3
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

```

Would I be right in thinking you use a VGA connection for the monitor?

I cannot quickly see any posts suggesting serious limitations.
You could looking in the man pages for i915, or investigate the properties of your monitor - the monitor gets queried at bootup (normally) to get a profile of what can be achieved, and uses this in conjunction with the video chipset limitations to work out what is the maximum you can get.

HTH

---

### Post by soreyes on 2011-12-10
> **dandnsmith said:**
> Would I be right in thinking you use a VGA connection for the monitor?

I cannot quickly see any posts suggesting serious limitations.
You could looking in the man pages for i915, or investigate the properties of your monitor - the monitor gets queried at bootup (normally) to get a profile of what can be achieved, and uses this in conjunction with the video chipset limitations to work out what is the maximum you can get.

HTH
Yes, that's right. 

I don't think that the problem is with the monitor. I used to have Windows and the screen was just fine; I think my resolution was 1280x1024. The problem is with Ubuntu - it doesn't let me change the resolution. It just gives me that one option in Settings and it's obviously not a good one.

---

### Post by dandnsmith on 2011-12-11
I cannot think of anything you can do, apart from chasing the idea that the i915 driver you have may not be the latest, and therefore lacks some capability.
A quick search on 'linux i915 driver' led me to [this page](http://intellinuxgraphics.org/) which might get you further - if you feel so inclined. The one proviso is that the monitor data reported to the kernel/driver/setup may not be ip to scratch (but I'd rule that out if Windows gave the higher resolution straightaway).

HTH

---

### Post by soreyes on 2011-12-13
I actually managed to change my resolution using the instructions here:
[http://www.myapitips.com/2011/11/02/how-to-change-monitor-resolution-in-ubuntu-11-10/](http://www.myapitips.com/2011/11/02/how-to-change-monitor-resolution-in-ubuntu-11-10/)

The strange thing now is, while everything looks fine on my desktop, menus, etc., the resolution still doesn't look right when I browse the internet. The letters are too small, and not very clear. Does that mean I haven't selected the right one? If so, how do I figure out what is my optimal resolution?

---

### Post by dandnsmith on 2011-12-14
That means you will want to fiddle with the font size settings in the browser (a quick adjustment for FireFox is ctrl with + or -) to see if that helps. If increasing the font size doesn't help, or doesn't change the fuzziness satisfactorily, then you may have to revert to previous resolution. It's really a personal choice thing (look at images also, to see how they appear).

---

