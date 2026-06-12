---
title: "Out of memory; kill Xorg; auto-logout"
date: 2011-08-22
forum: General Help
---

### Post by jgm101k1 on 2011-08-22
Ubuntu 11.04

Leaving the screen locked, the system will ultimately auto-logout.  At the time of the logout, as discerned from the "last" command, I find in the syslog, for example:

Aug 20 21:24:19 dev-1 kernel: [805641.867863] Out of memory: Kill process 32602 (Xorg) score 17 or sacrifice child
Aug 20 21:24:20 dev-1 kernel: [805641.867871] Killed process 32602 (Xorg) total-vm:371200kB, anon-rss:37932kB, file-rss:292kB

This is experienced every day or two--usually within one hour of locking the screen, but not always.  It can be more than one day after locking the screen.

The only change to the system was the addition of a video card which, by system design, disables the on board video.   Below is some video card information.

Thank you in advance for any feedback or guidance.

Jim


_lspci | grep VGA_
03:00.0 VGA compatible controller: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)

_sudo lshw_
...
id:	
display
description:	VGA compatible controller
product:	NV44 [Quadro NVS 285]
vendor:	nVidia Corporation
physical id:	
0
bus info:	
pci@0000:03:00.0
version:	a1
width:	64 bits
clock:	33MHz
capabilities:	pm msi pciexpress vga_controller bus_master cap_list rom
configuration:	
driver	=	nvidia
latency	=	0
resources:	
irq	:	16
memory	:	f8000000-f8ffffff
memory	:	d0000000-dfffffff
memory	:	f9000000-f9ffffff
memory	:	fa000000-fa01ffff
...

---

