---
title: "Problem - Ubuntu not recognising 2nd monitor"
date: 2012-07-14
forum: General Help
---

### Post by Andrew F in Australia on 2012-07-14
Hi All,

A weird one that I would appreciate any assistance or advice with please.

Am running a dual boot Zalman HD160 case as a music server, windows 7 and Ubuntu.  I prefer Linux but can not get dual monitors to work ( but they do using the exact same hardware in Windows.)

The monitor inbuilt into the front of the server is a small 8" or thereabouts LCD screen, that Ubuntu detects as  a laptop screen.

The graphics card is a nvidia Geforce 8400GS - both Windows and Ubuntu 12.04 only detect a single display under the Nvidia controller/control panel.

The outputs from the graphics card ar a VGA and a DVI output (connected through an adapter to a VGA monitor.)

It does not matter which output I connect video jacks to, the small LCD screen is the only one that's detected.

However, I can enable the VGA monitor in windows by using the generic settings panel control panel | display| screen resolution ( Windows.) so that I can access duplicate displays.  The fact that both Ubuntu and Windows detect only one monitor in nvidia indicates to me that it's not the nvidia drivers but more an Ubuntu issue.

No matter what I do in ubuntu Im unable to connect dual monitors. NVIDIA X Server settings only gives one monitor option, highlighted as a "laptop"

Have enabled the **ppa:ubuntu-x-swat/x-updates** repositories and am running current Nvidia drivers.

some output from terminal enquiries such as lspci randr, etc below.

Any advice that you are able to provide is greatly appreciated to try and get two monitors recognised in Ubuntu - happy to run any terminal enquiries etc... that are needed.

Cheers,

AF

```
horace-music@horacemusic-System-Product-Name:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. Attansic L1 Gigabit Ethernet (rev b0)
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:00.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
04:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
horace-music@horacemusic-System-Product-Name:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0  
   720x450        52.0  
   680x384        53.0     54.0  
   640x480        55.0     56.0  
   512x384        57.0  
   320x240        58.0  
horace-music@horacemusic-System-Product-Name:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07b8:b21d AboCom Systems Inc RT2573
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 15c2:0034 SoundGraph Inc. 
Bus 005 Device 002: ID 04b3:3025 IBM Corp. 
Bus 005 Device 003: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded
horace-music@horacemusic-System-Product-Name:~$ 

```

---

### Post by flipper T on 2012-07-14
in NVIDIA X Server settings, have you tried pressing the "detect displays" button ?

---

### Post by Andrew F in Australia on 2012-07-14
> **flipper T said:**
> in NVIDIA X Server settings, have you tried pressing the "detect displays" button ?

Hi Flipper,

Sorry, yes I did, in both Windows and Ubuntu - didn't work in either so I discounted it as a factor.

Has anybody come across this before, or does anyone know of a solution?

Cheers,

AF

---

### Post by Andrew F in Australia on 2012-07-14
HI All,

Should add that the System Settings | Display in Ubuntu fails to recognise the second monitor also.

Any ideas?

Cheers,

AF

---

