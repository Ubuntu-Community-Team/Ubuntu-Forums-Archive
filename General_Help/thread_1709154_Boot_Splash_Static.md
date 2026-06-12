---
title: "Boot Splash Static"
date: 2011-03-17
forum: General Help
---

### Post by Rpdiddy on 2011-03-17
Upon boot up the usual little mouse splash boot is SUPPOSE to come up. Once I first installed it (10.10 via usb) the boot screen worked perfectly but after i updated via the update manager the boot splash became all static and green lines across the image. It still boots up to the login screen but it's just ugly looking at it. 
I have (via hwinfo)
20: PCI 105.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_5a61
  Unique ID: ul7N.dFXV26GrjA4
  Parent ID: vSkL.CTscIjbcyd9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "ATI Radeon XPRESS 200 5A61 (PCIE)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x5a61 "Radeon XPRESS 200 5A61 (PCIE)"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a3d 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  I/O Ports: 0xd000-0xdfff (rw)
  Memory Range: 0xfeaf0000-0xfeafffff (rw,non-prefetchable)
  Memory Range: 0xfeac0000-0xfeadffff (ro,non-prefetchable,disabled)
  IRQ: 17 (51901 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00005A61sv0000103Csd00002A3Dbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: fglrx
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #9 (PCI bridge)

Primary display adapter: #20

ANY HELP?

---

### Post by JC Cheloven on 2011-03-17
It appear to be an issue with the driver for your graphics driver. I'm not sure, but it seems to be an ati/raedon, right? To be sure please look at the output of
```
lspci
``` (search for something starting by VGA)

If so, you can disable the driver (system-administration-hardwae drivers), reboot to test that the ugly lines disappeared, and thentrying to activate a different driver (same menu as above), if some choice is offered.

Perhaps the output of lspci could give us some additional clue.

---

### Post by JKyleOKC on 2011-03-17
Did your upgrade include one or more new kernel packages? If so, you may have run into kernel changes that are apparently not fully compatible with some video drivers.

You can test if this is what happened quite easily, by editing the GRUB menu entry at boot time, although you may have to increase the menu display time. If you don't usually see the grub menu, press the left shift key during the boot sequence. It may take several tries to hit the short time window, but when you get the menu displayed, select the topmost entry and press "e" to enter the editor. This will display the entire boot script for that choice; one of the lines will contain the words "quiet" and "splash" near its end. Select that line and press "e" again to edit it, then arrow over to the word "splash" and add the word "nomodeset" after it, inside the quote marks and separated by a space. Then press CTRL-X to continue booting.

What this does is turn OFF the portion of the boot code that runs into that incompatibility, so if that's your problem, the screen should look perfectly normal again for the remainder of the session. However it's only temporary and will go away when you restart, so if it doesn't work you can just restart and nothing will be harmed.

If it does solve the problem, let us know and I can then tell you how to make the change permanent by editing a single configuration file. However there's no need to go into all that detail unless it will help...

---

### Post by Rpdiddy on 2011-03-18
Ok I've tried this but it doesn't appear to work and I need to turn off my computer everyday. Could you tell me the permanent method because I can't keep looking at the static (it kinda hurts my eyes).

---

### Post by JKyleOKC on 2011-03-18
If it didn't work, then the permanent version wouldn't either -- it would just insert the "nomodeset" option automatically.

There are a number of other possibilities as to what could be happening. Using an older kernel might solve the problem for you. Get to the grub menu as before, then scroll down to the third line (you can see that the first two lines are for the same version number but the second is for recovery mode; the menu follows that pattern for all the kernel versions you have installed). If that gets rid of the static, we can make it be the automatic choice. If it doesn't, and there are even older kernel versions shown, try the fifth line, seventh, and so on.

If you find one that works, let us know which one it is and we'll show you how to edit the /etc/default/grub file to make it the automatic choice. If not, then there are still more things to try...

---

