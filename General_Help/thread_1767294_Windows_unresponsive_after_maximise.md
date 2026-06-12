---
title: "Windows unresponsive after maximise"
date: 2011-05-25
forum: General Help
---

### Post by tazzik on 2011-05-25
A window is working fine.

I minimise it, no problems - do something else, no problems.

When I maximise the minimised window, it maximises but does not react to any input - it appears frozen. 
For instance, if I were to maximise a previously minimised google page click the search text box nothing would happen - the cursor would not blink, the focus would not shift to the text box. If I typed "blah blah blah" nothing would happen.

If I minimise the window then re-maximise it, suddenly the text box has focus and "blah blah blah" is sitting there.


This leads me to believe it is a Compiz problem since the progam continues to work in the background, it is as though the picture of the program is not being updated.

I didn't used to have this problem and I don't think I changed anything when it suddenly arose.

Any ideas??

(Ubuntu 11.04 x86)

---

### Post by tazzik on 2011-05-28
Bump?
Any ideas?

---

### Post by tazzik on 2011-05-29
Still a very annoying problem, any suggestions?

---

### Post by wildmanne39 on 2011-05-29
> **tazzik said:**
> Still a very annoying problem, any suggestions?

Hi, what are your system  specs? What version of ubuntu are you using? Are you using the cube or effects? Is your system new or old? Put this command in terminal      
```
lspci
```copy and paste it here by clicking new reply then above the window you type in click on # and put the information in between the 2 code boxes ```

```

---

### Post by tazzik on 2011-05-30
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman PRO [AMD Radeon 6900 Series]
01:00.1 Audio device: ATI Technologies Inc Device aa80
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 SATA controller: JMicron Technology Corp. JMB362 AHCI Controller (rev 10)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
07:00.0 PCI bridge: Device 1b21:1080 (rev 01)
09:00.0 SATA controller: Marvell Technology Group Ltd. Device 9172 (rev 11)
```

Specs are: Core i7 2600K, 4GB DDR3 RAM, ATI HD6970 (proprietary drivers), Asus P8P67 Pro.

No compiz cube, and not many effects, I will list the enabled ones here:
Commands
Composite
Gnome Compatibility
OpenGL
Enhanced Zoom Desktop
Magnifier
Opacity, Brightness and Saturation
Desktop Wall
Expo
Viewport Switcher
Animations
Fading Windows
Window Decoration
Png
Bailer
Compiz Library Toolbox
Detection
Regex Matching
Session Management
Mouse Position Polling
Workarounds
Grid
Move Window
Place Windows
Resize Window
Scale
Snapping Windows
Static Application Switcher

I don't think I've enabled any of these myself, I think they were all enabled by default.

---

### Post by tazzik on 2011-06-01
Still having problems. Ideas?

---

