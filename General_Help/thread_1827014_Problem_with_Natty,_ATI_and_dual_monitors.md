---
title: "Problem with Natty, ATI and dual monitors"
date: 2011-08-17
forum: General Help
---

### Post by kloper on 2011-08-17
Hi all!

I have a Dell Optiplex 980 and two Dell 2007 FPb monitors at work, so I'm trying to setup this dual monitor thingy in Ubuntu Natty 11.04. See the technical info below.

The result is that one screen shows the Unity desktop, and the other screen shows the "Ubuntu boot screen" (the Ubuntu logo with five orange dots underneath).

I have followed the [Ubuntu installation guide]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Dual.2FMulti_Monitors") about ATI and dual monitors. I have installed the glx and jockey packages, and I have also downloaded and installed the driver from ati.com.

Can anyone see what I am doing wrong here?

Also, fgl_glxgears shows a rotating cube that is rotating far from smoothly. And it takes 30 seconds to get to the desktop from the login screen...


lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
```

xrandr:

```
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0*+
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x960       60.0 +   75.0  
   1152x864       60.0 +   75.0  
   1152x648       60.0 +
   1280x1024      75.0     60.0  
   1280x800       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
```

xorg.conf:

```
Section "ServerLayout"
        Identifier     "Dual monitors"
        Screen         "screen0"
        Screen         "screen1" RightOf "screen0"
        Option         "Xinerama"
EndSection

Section "Monitor"
        Identifier  "monitor0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier  "monitor1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ati0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      0
EndSection

Section "Device"
        Identifier  "ati1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "screen0"
        Device     "ati0"
        Monitor    "monitor0"
        DefaultDepth     24
        SubSection "Display"
#               Viewport   0 0
                Depth      24
                Modes      "1600x1200"
        EndSubSection
EndSection

Section "Screen"
        Identifier "screen1"
        Device     "ati1"
        Monitor    "monitor1"
        DefaultDepth     24
        SubSection "Display"
#               Viewport   0 0
                Depth      24
                Modes      "1600x1200"
        EndSubSection
EndSection
```

fglrxinfo:

```
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4550   
OpenGL version string: 3.3.10907 Compatibility Profile Context
```

fgl_glxgears:

```
Using GLX_SGIX_pbuffer
6004 frames in 5.0 seconds = 1200.800 FPS
```

---

