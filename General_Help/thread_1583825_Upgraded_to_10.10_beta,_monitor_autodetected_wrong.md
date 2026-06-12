---
title: "Upgraded to 10.10 beta, monitor autodetected wrong resolution"
date: 2010-09-28
forum: General Help
---

### Post by pseudocube on 2010-09-28
After an upgrade to 10.10, even though my max resolution is 1024x1280(**Edit: strike that, reverse it**), the default configuration is 1024x768 at 60Hz, with only 1360x768, 800x600, 848x480, and 640x480 listed as alternatives. The monitor is not recognized, it's labelled "unknown." **Edit**: it's a Princeton VL1919.

Additionally, xorg.conf doesn't exist.

```
andrew@andrew-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
andrew@andrew-desktop:~$ 

```

Following the instructions here ([https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions)) did not work. See below.

```
andrew@andrew-desktop:~$ cvt 1024 1280
# 1024x1280 59.97 Hz (CVT) hsync: 79.58 kHz; pclk: 109.50 MHz
Modeline "1024x1280_60.00"  109.50  1024 1096 1200 1376  1280 1283 1293 1327 -hsync +vsync
andrew@andrew-desktop:~$ xrandr --newmode "1024x1280_60.00"  109.50  1024 1096 1200 1376  1280 1283 1293 1327 -hsync +vsync
andrew@andrew-desktop:~$ xrandr --output VGA1 --mode 1024x1280
xrandr: cannot find mode 1024x1280
andrew@andrew-desktop:~$ 

```

---

### Post by rhoparkour on 2010-09-28
Really have no solution for you, but I'll say something stupid just in case:

Have you tried System > Preferences > Monitors? I've messed around with that sometimes and it  has options to change resolutions....

---

### Post by pseudocube on 2010-09-29
> **rhoparkour said:**
> Really have no solution for you, but I'll say something stupid just in case:

Have you tried System > Preferences > Monitors? I've messed around with that sometimes and it  has options to change resolutions....


That was the very first thing I tried. :???: Thank you for the reply, though.

---

### Post by QIII on 2010-09-29
Remember thay Maverick is a Beta.  There is forum for it.

What are your hardware specs and what video driver are you using?

Your resolition numbers also look odd.

---

### Post by pseudocube on 2010-09-29
> **QIII said:**
> Remember thay Maverick is a Beta.  There is forum for it.
I'm sorry. I didn't know that. There are a couple other bugs I've found; should I post them there or file a bug report?

> **QIII said:**
> What are your hardware specs [...]?
I'm using a Dell Dimension 3000. ([Specs]("http://support.dell.com/support/edocs/systems/dim3000/en/SM/specs.htm#wp1075776")) I'd rather have used Sysinfo, but it [keeps crashing]("https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727").

> **QIII said:**
> [...]and what video driver are you using?

Is this what you need?
```
andrew@andrew-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: Dell Device 019d
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell Dimension 3000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ed98 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Device 019d
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Device 019d
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
	Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:02.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
	Subsystem: Device 4942:4c4c
	Flags: bus master, slow devsel, latency 64, IRQ 17
	I/O ports at df00 [size=64]
	Kernel driver in use: ENS1370
	Kernel modules: snd-ens1370

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Dell Dimension 3000
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at df40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

andrew@andrew-desktop:~$ 
```

---

### Post by QIII on 2010-09-29
OK.  I'll have to check if there is anything interesting about that chipset.  Looks like it should work unless there is a problem.

Look again at the resolution you are trying to set.  It is taller than it is wide.

---

### Post by pseudocube on 2010-09-30
Ah, thanks for pointing out my mistake. It IS actually 1280x1024 I'm trying to get.

Here I did my initial attempt at fixing it, but with the resolution I meant to use:

```
andrew@andrew-desktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
andrew@andrew-desktop:~$ xrandr --newmode Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
andrew@andrew-desktop:~$ xrandr --output VGA1 --mode 1280x1024
xrandr: cannot find mode 1280x1024

```

Didn't fix it this time around either. :/

---

### Post by pseudocube on 2010-10-02
I've decided to reinstall 10.04, then try out 10.10 on a Live CD after it comes out to see if the bugs I am experiencing are still there. Hopefully, they will be gone by the time the stable version is out.

I just can't keep using my computer in such a tiny resolution. So I'm very sorry if I can't help you out any more if you happen to need more information on the bug.

---

### Post by lion.guo on 2010-10-05
my monitor is 1440x900, but at 10.10 I got 1024x768

lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
    Subsystem: nVidia Corporation Device cb84
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at fc00 [size=64]
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
    Subsystem: nVidia Corporation Device cb84
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fd800000-fd8fffff
    Prefetchable memory behind bridge: fdf00000-fdffffff
    Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
    Subsystem: nVidia Corporation MCP61 High Definition Audio
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at dc00 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fde00000-fdefffff
    Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at cc00 [size=256]
    Memory at fd8ff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

---

### Post by pseudocube on 2010-11-20
About a week ago I downloaded Ubuntu again and tried in in a LiveCD. The problem still exists.

---

### Post by pseudocube on 2010-12-25
It's been ages, guys. :( Just tried it, and it's still there! What can I do?

---

