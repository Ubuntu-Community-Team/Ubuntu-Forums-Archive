---
title: "Problems with Display in 11.04"
date: 2011-05-31
forum: General Help
---

### Post by mbusha on 2011-05-31
I recently upgraded (from 10.44, I think) to 11.04 on a Lenovo Thinkpad T510 and have been having issues with my display every since.  Primarily, I'm unable to plug my computer to an external monitor.  Whenever I plug in try to export the settings (using Fn-F7), both monitors go black, but I can see the mouse cursor and move it around.  I can continue to cycle through the display settings, and the mouse course moves to appearing on just one display, then the other, being mirrored, etc, but the screens stays blank -- even after I unplug the external monitor.  The computer seems to be working, since if I have a terminal window open, I can type "sudo shutdown -r 0" and get the computer to restart, even though the monitor is blank.  A restart seems to be the only fix I've found so far.  

I occassionally get a similar problem when coming out of the screensaver mode.  The last image of the screensaver will be frozen on the screen, but I can see/move my mouse cursor and (if a terminal window is open), restart the system.  

Any thoughts what could be going on here?

---

### Post by mbusha on 2011-06-10
I wound up formatting/reinstalling 11.04 onto a clean hard drive, but these problems seem to still be there.  I haven't noticed the freeze up when coming out of the screen saver, but I still have some of the other similar problems:

1.  Sometimes the focus will get stuck on a single window.  This usually happens with either opening a new terminal window, or switching between Workspaces.  I can move my mouse cursor around, but am unable to click on anything or get the focus out of the active window.   I can open a new program using shortcuts (i.e., ctrl-shift-n to open a new terminal window).  The focus then becomes stuck on the new terminal window.  I've discovered that if I exit out of the terminal via the command line, things are usually restored, although sometimes the focus just gets stuck on the next terminal window that becomes active by default after the first closes.  

2.  When plugging into an external monitor, usually both monitors just go blank except for the mouse cursor that I can move around.  The computer still seems to be running since if I have a terminal window open before I do this, I can usually still type "sudo shutdown -r 0" and get the computer to restart.  

Anyone have any thoughts about this?  Here's some additional information on my system that may be relevant.

Display information:

```
$ sudo lshw -C Display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)

```

and more general hardware information from a lspci command:

```
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

