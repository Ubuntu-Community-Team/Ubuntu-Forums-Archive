---
title: "HP Compaq NC8000 Screen Goes Blank except for Mouse Pointer &amp; Cursor &amp; Crashes"
date: 2010-06-03
forum: General Help
---

### Post by elmy on 2010-06-03
Hi everyone, Did a quick search for these symptoms and couldn't find anything related.

After upgrading to 10.04 I found that the computer (HP NC8000) now crashes frequently and at random intervals. It occurs sometimes after only a few minutes, other times after an hour or two.

It happens while its in use, or while its idle, wether the screensaver is on or not, even if its locked and the lid closed. When I walk away and come back I find the screen has gone blank (except for the Mouse Pointer and a cursor in the top left) and the Caps Lock Light and Num Lock Light are flashing (signifying a crash)

I caught it while I was using it and watched as the screen suddenly went blank as described above. No errors or explanations or warning.

A reboot restores order, but not for long.

Some assistance with diagnosing this would be helpful. I suspect it could be ATI radeon 9600 mobility related, as with each passing version of ubuntu it seems to be more unstable

regards
Andrew

---

### Post by -humanaut- on 2010-06-03
Type this in a terminal and post back the results

lspci -v

---

### Post by elmy on 2010-06-03
> **-humanaut- said:**
> Type this in a terminal and post back the results

lspci -v

Hi -humanaut- as requested:-

elminster@ODYSSEY:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, fast devsel, latency 0
	Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 90400000-904fffff
	Prefetchable memory behind bridge: 98000000-9fffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 3c00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0c, sec-latency=32
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: 90000000-903fffff
	Prefetchable memory behind bridge: 40000000-4dffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 3c20 [size=16]
	Memory at 4e000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: medium devsel
	I/O ports at 1200 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 3000 [size=256]
	I/O ports at 3880 [size=64]
	Memory at a0100000 (32-bit, non-prefetchable) [size=512]
	Memory at a0180000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: medium devsel, IRQ 11
	I/O ports at 3400 [size=256]
	I/O ports at 3800 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

02:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Compaq Computer Corporation Device 00e5
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 90080000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90180000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 50000000-53fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90200000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 44000000-47fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: slow devsel, IRQ 10
	Memory at 90280000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 48000000-4bfff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 90380000 (32-bit, non-prefetchable) [size=2K]
	Memory at 90100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 90000000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 4c000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

elminster@ODYSSEY:~$ sudo lspci -v
[sudo] password for elminster: 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, fast devsel, latency 0
	Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: [e4] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 2.0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 90400000-904fffff
	Prefetchable memory behind bridge: 98000000-9fffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38c0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 38e0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 3c00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0c, sec-latency=32
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: 90000000-903fffff
	Prefetchable memory behind bridge: 40000000-4dffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 3c20 [size=16]
	Memory at 4e000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: medium devsel
	I/O ports at 1200 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 3000 [size=256]
	I/O ports at 3880 [size=64]
	Memory at a0100000 (32-bit, non-prefetchable) [size=512]
	Memory at a0180000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: medium devsel, IRQ 11
	I/O ports at 3400 [size=256]
	I/O ports at 3800 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

02:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Compaq Computer Corporation Device 00e5
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 90080000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath5k
	Kernel modules: ath5k

02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90180000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 50000000-53fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90200000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 44000000-47fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: slow devsel, IRQ 10
	Memory at 90280000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 90300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 48000000-4bfff000 (prefetchable)
	Memory window 1: 58000000-5bfff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 90380000 (32-bit, non-prefetchable) [size=2K]
	Memory at 90100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
	Subsystem: Hewlett-Packard Company Device 088c
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at 90000000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 4c000000 [disabled] [size=64K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

---

### Post by elmy on 2010-06-03
Some additional info regarding my problem.

I can replicate the problem at will by running System Testing.

Every time I attempt it, the blank screen (with mouse pointer and cursor only) followed by a crash occurs.

It happens during the gathering info part of the Test after you click on the first "next" prompt.

Something in there is definitely misbehaving. There are no propriety drivers in use on the system. My Compiz-Fusion Desktop still spins, OpenGL apps still flicker just like they used to on all all previous versions of ubuntu, Everything works initially, just suddenly it locks up.

Smoothest upgrade I've had really. Even the Wifi card survived the upgrade this time. Not sure if my issue is hardware related or a creeping incompatibility due to the age of the laptop and its legacy nature. I'm only running 1Gig of RAM but I used to only run 512Meg back in early Ubuntu 6.04 days.

On previous ubuntus Cairo Dock would always end in a crash no matter what version of ubuntu I used, so I stopped using it. Sometimes in ubuntu 9.10 it would crash when I opened more than 4 or 5 tabs in Mozilla. This was less frequent when I scrapped cairo dock though. Its only now on 10.04 that its become a frequent problem rather than an occasional nuisance.

Its for the above reasons I suspect the ATI radeon 9600 mobility. Its the been the most troublsome aspect historically. With every release I struggle between accepting the ubuntu standard GFX drivers, or trying to fiddle around with fglrx and ATI Drivers for Linux from amd. I always settle on the ubuntu open driver as its the only one that allows compiz-fusion to work.

---

### Post by dino99 on 2010-06-03
several things to check:

- goto system admin hardware driver to see if your driver is activated (which one is installed ?)

- into /home, unhide files into menu, and look at .xsession-errors

- into system admin log viewer: check xorg.log, system.log and user.log

- see if disabling compiz and other eyecandy stuff help or not

---

### Post by elmy on 2010-06-03
> **dino99 said:**
> several things to check:

- goto system admin hardware driver to see if your driver is activated (which one is installed ?)

- into /home, unhide files into menu, and look at .xsession-errors

- into system admin log viewer: check xorg.log, system.log and user.log

- see if disabling compiz and other eyecandy stuff help or not

Hi dino99

System admin hardware driver - says no drivers (and nothing listed to choose from)

.xsession-errors shows:-

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1140]: EggSMClient-WARNING: Desktop file '/home/elminster/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
SSH_AUTH_SOCK=/tmp/keyring-xYmE6v/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
SSH_AUTH_SOCK=/tmp/keyring-xYmE6v/ssh

(polkit-gnome-authentication-agent-1:1232): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1232): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1

(gnome-power-manager:1236): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x92a8c70'
** (nm-applet:1233): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1233): DEBUG: old state indicates that this was not a disconnect 0
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/elminster/.compiz/session/10b1666a10cd3fd88d127557070820760400000011400028"

(bluetooth-applet:1234): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(nm-applet:1233): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(gnome-power-manager:1236): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

** (gnome-screensaver:1284): WARNING **: screensaver already running in this session
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
** (nm-applet:1233): DEBUG: foo_client_state_changed_cb
** (nm-applet:1233): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 2859 1275573600 1275570741
evolution-alarm-notify-Message:  Fri Jun  4 00:00:00 2010

evolution-alarm-notify-Message:  Thu Jun  3 23:12:21 2010



It also shows lots of:

(firefox-bin:1339): Gdk-WARNING **: XID collision, trouble ahead
** (update-notifier:1440): DEBUG: Skipping reboot required

on the last line (most likely because I have the browser open typing this.

Interesting there are some lines there about compiz, and the screensaver. I will turn all off.

regards

Andrew

---

### Post by dino99 on 2010-06-03
> **elmy said:**
> Hi dino99

System admin hardware driver - says no drivers (and nothing listed to choose from)

.xsession-errors shows:-

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
gnome-session[1140]: EggSMClient-WARNING: Desktop file '/home/elminster/.config/autostart/cairo-dock-cairo.desktop' has malformed Icon key 'cairo-dock.svg'([COLOR="Red"]should not include extension[/COLOR])
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
SSH_AUTH_SOCK=/tmp/keyring-xYmE6v/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-xYmE6v
SSH_AUTH_SOCK=/tmp/keyring-xYmE6v/ssh

(polkit-gnome-authentication-agent-1:1232): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1232): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1

(gnome-power-manager:1236): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x92a8c70'
** (nm-applet:1233): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1233): DEBUG: old state indicates that this was not a disconnect 0
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/elminster/.compiz/session/10b1666a10cd3fd88d127557070820760400000011400028"

(bluetooth-applet:1234): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(nm-applet:1233): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(gnome-power-manager:1236): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

** (gnome-screensaver:1284): WARNING **: screensaver already running in this session
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
** (nm-applet:1233): DEBUG: foo_client_state_changed_cb
** (nm-applet:1233): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 2859 1275573600 1275570741
evolution-alarm-notify-Message:  Fri Jun  4 00:00:00 2010

evolution-alarm-notify-Message:  Thu Jun  3 23:12:21 2010



It also shows lots of:

(firefox-bin:1339): Gdk-WARNING **: XID collision, trouble ahead
** (update-notifier:1440): DEBUG: Skipping reboot required

on the last line (most likely because I have the browser open typing this.

Interesting there are some lines there about compiz, and the screensaver. I will turn all off.

regards

Andrew

see above for cairo error, remove/purge it into synaptic (right click) then reinstall

remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

into synaptic: xserver-xorg-video-radeon need to be installed

reboot, then check again if driver is activated

[http://art.ubuntuforums.org/showthread.php?t=1475024](http://art.ubuntuforums.org/showthread.php?t=1475024)

---

### Post by elmy on 2010-06-04
> **dino99 said:**
> see above for cairo error, remove/purge it into synaptic (right click) then reinstall

remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

into synaptic: xserver-xorg-video-radeon need to be installed

reboot, then check again if driver is activated

[http://art.ubuntuforums.org/showthread.php?t=1475024](http://art.ubuntuforums.org/showthread.php?t=1475024)


Hi dino99

I have done the above, I noticed in Synaptic that xserver-xorg-video-radeon was already installed. I removed it and then reinstalled it.

However after rebooting there is still nothing listed in the Hardware Drivers for me to activate.

I still have to review the other 3 logs you mentioned. I turned off Compiz, and was about to reply advising that it seemed to have improved as it had gone 24 hours without crashing...., when it crashed! 8-)

regards
elmy000

---

