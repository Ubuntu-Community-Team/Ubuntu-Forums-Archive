---
title: "Help! White screen after login"
date: 2006-04-01
forum: General Help
---

### Post by elvez on 2006-04-01
I have a serious problem, I think. Everything has worked just fine for several months, but today, after login in the screen goes white. The mouse cursor in normal (arrow) and it is not frozen. I can choose to logging in with just the terminal, but I dont know what I can do to fix this

I have no idea how this happend. I am wery unexperienced with Linux in general, so an easy solution (if possible) would be preferred.

I am running Breezy on an HP pavilion laptop.

---

### Post by dermotti on 2006-04-01
So the login screen looks fine, but after you enter username and password everything goes crazy?

---

### Post by elvez on 2006-04-01
[QUOTE=dermotti]So the login screen looks fine, but after you enter username and password everything goes crazy?[/QUOTE]

Yes. Nothing happens. it is just white (maybe brown if default settings)

---

### Post by Ramses de Norre on 2006-04-01
Are there any errors in /var/log/Xorg.0.log or ~/.xsession-errors ?

---

### Post by elvez on 2006-04-01
In terminal, typing "X", I get: 

Fatal server error: Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again

Thanks for all replys!

---

### Post by Ramses de Norre on 2006-04-01
```
less /var/log/Xorg.0.log
less ~/.xsession-errors

```
Post the outputs.

---

### Post by elvez on 2006-04-01
I would, but the log file is quite long and I am in a hurry right now. (Got to go!! I will check in later).  There is 11 lines with WARNING at the bottom and the say ex. ".pcf" already registered at priority 0 . The rest of the lines says the same about: .pcf .Z , .pcf.gz , .snf , .snf.Z , .snf gz , .bdf , bdf.Z , .bdf.gz and .pmf

I dont want to sound unthankful, but I have to go now. I am actually at a conference, and everything is a caos because of my little problem.

As i said earlier. Thank you all. I'll be back :-)


EDIT 1 minute after:

I hit alt + ctrl +f7 And  I was logged in, and everythin is apparently fine.
I dont have the guts to restart the macine yet, but it seems that it just took some time to start up everything after logging in. Any idea why?

---

### Post by elvez on 2006-04-01
[QUOTE=Ramses de Norre]```
less /var/log/Xorg.0.log
less ~/.xsession-errors

```
Post the outputs.[/QUOTE]

As I said earlier, it doesn't hang after login. This white screen lasts for about 6 to 7 minutes before everything start to work. This happens everytime I reboot.


Here is my" .xsession-errors" output

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kjell"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/hplaptop:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/hplaptop:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/hplaptop:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/hplaptop:/tmp/.ICE-unix/8103

** (gnome-session:8103): WARNING **: Esound failed to start.

manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject

** (gnome-session:8103): WARNING **: Host name lookup failure on localhost.

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported

eth0      Interface doesn't support scanning : Operation not supported


** (gnome-cups-icon:8250): WARNING **: IPP request failed with status 1280
Malformed attributes:  HTML PUBLIC "-//IETF//DTD HTML 2.0//EN" found in:
 HTML PUBLIC "-//IETF//DTD HTML 2.0//EN"
Current stack: :!DOCTYPE
Malformed attributes:  HTML PUBLIC "-//IETF//DTD HTML 2.0//EN" found in:
 HTML PUBLIC "-//IETF//DTD HTML 2.0//EN"
Current stack: :!DOCTYPE

** (gnome-cups-icon:8250): WARNING **: IPP request failed with status 1280
Warning: more than one line!

(gnome-terminal:8656): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8656): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Warning: more than one line!

(gnome-terminal:8721): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8721): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

---

### Post by elvez on 2006-04-01
And here is the "xorg.0.log" output

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux hplaptop 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:13:17 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr  2 00:43:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,cbb2 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,7010 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10b9,5451 card 103c,0850 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 10b9,1533 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,5457 card 103c,0850 rev 00 class 07,03,00 hdr 00
(II) PCI: 00:09:0: chip 1260,3873 card 1468,0200 rev 01 class 02,80,00 hdr 00
(II) PCI: 00:0a:0: chip 1217,6972 card 1c01,0000 rev 00 class 06,07,00 hdr 02
(II) PCI: 00:0b:0: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:0b:1: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:0b:2: chip 1106,3104 card 0925,1234 rev 51 class 0c,03,20 hdr 80
(II) PCI: 00:0c:0: chip 104c,8026 card 103c,0850 rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:10:0: chip 10b9,5229 card 103c,0850 rev c4 class 01,01,fa hdr 00
(II) PCI: 00:11:0: chip 10b9,7101 card 103c,0850 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 100b,0020 card 103c,0850 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:05:0: chip 1002,4337 card 103c,0850 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0300000 - 0xd03fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc Radeon IGP 340M rev 0, Mem @ 0xd8000000/27, 0xd0300000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd4000000 from 0xd7ffffff to 0xd3ffffff
(II) PCI Memory resource overlap reduced 0xd0009000 from 0xd0009fff to 0xd0008fff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[1] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[2] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[3] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[4] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[5] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[7] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[8] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[9] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[12] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[13] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[14] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[1] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[2] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[3] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[4] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[5] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[6] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[7] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[8] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[9] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[11] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[12] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[13] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[14] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[7] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[8] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[9] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[10] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[12] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[13] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[14] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[20] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[21] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:05:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)".
(--) Chipset ATI Radeon IGP330M/340M/350M (U2) 4337 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[7] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[8] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[9] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[10] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[12] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[13] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[14] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[20] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[21] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)

---

### Post by elvez on 2006-04-01
...and it continues.....

(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[7] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[8] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[9] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[10] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[12] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[13] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[14] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[23] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[24] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[25] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[26] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[27] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xd0300000
(II) RADEON(0): PCI bus 1 card 5 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon IGP330M/340M/350M (U2) 4337" (ChipID = 0x4337)
(--) RADEON(0): Linear framebuffer at 0xd8000000
(--) RADEON(0): VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): LVDS port is not in connector table, added in.
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Connector0: DDCType-5, DACType-1, TMDSType--1, ConnectorType-1
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- Proprietary
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- NONE
 DDC Type  -- Unknown
(II) RADEON(0): PLL parameters: rf=1432 rd=31 min=12000 max=35000; xclk=13300
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: QDI141X1LH03            
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1024x768
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1024x768 (pitch 1024)
(**) RADEON(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1040 1176 1344  768 770 771 806
(**) RADEON(0):  Default mode "640x350": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x350"   65.00  640 1040 1176 1344  350 770 771 806
(**) RADEON(0):  Default mode "640x400": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x400"   65.00  640 1040 1176 1344  400 770 771 806
(**) RADEON(0):  Default mode "720x400": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "720x400"   65.00  720 1040 1176 1344  400 770 771 806
(**) RADEON(0):  Default mode "640x480": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   65.00  640 1040 1176 1344  480 770 771 806
(**) RADEON(0):  Default mode "800x600": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "800x600"   65.00  800 1040 1176 1344  600 770 771 806
(**) RADEON(0):  Default mode "832x624": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "832x624"   65.00  832 1040 1176 1344  624 770 771 806
(==) RADEON(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0300000 - 0xd030ffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd0008000 - 0xd0008fff (0x1000) MX[B]
	[8] -1	0	0xd0004000 - 0xd0007fff (0x4000) MX[B]
	[9] -1	0	0xd0003800 - 0xd0003fff (0x800) MX[B]
	[10] -1	0	0xd0003000 - 0xd00030ff (0x100) MX[B]
	[11] -1	0	0xd000a000 - 0xd000afff (0x1000) MX[B]
	[12] -1	0	0xd0001000 - 0xd0001fff (0x1000) MX[B]
	[13] -1	0	0xd0000000 - 0xd0000fff (0x1000) MX[B]
	[14] -1	0	0xd0009000 - 0xd0008fff (0x0) MX[B]O
	[15] -1	0	0xd4000000 - 0xd3ffffff (0x0) MX[B]O
	[16] -1	0	0xd0300000 - 0xd030ffff (0x10000) MX[B](B)
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x00002040 - 0x0000204f (0x10) IX[B]
	[26] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[27] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[28] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[29] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[30] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
(II) RADEON(0): Dynamic Clock Scaling Disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [drm] loaded kernel module for "radeon" driver
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:05.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xdcc16000
(II) RADEON(0): [drm] mapped SAREA 0xdcc16000 to 0xb3d23000
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd4000000
(II) RADEON(0): [agp] Ring mapped at 0xb3c22000
(II) RADEON(0): [agp] ring read ptr handle = 0xd4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb3c21000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb3a21000
(II) RADEON(0): [agp] GART texture map handle = 0xd4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb3541000
(II) RADEON(0): [drm] register handle = 0xd0300000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1024,8191)
(II) RADEON(0): Reserved area from (0,768) to (1024,770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7421
(II) RADEON(0): Will use back buffer at offset 0xc00000
(II) RADEON(0): Will use depth buffer at offset 0xf00000
(II) RADEON(0): Will use 47104 kb for textures at offset 0x1200000
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 7417
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): X context handle = 0x00000001
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 10
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "no"
(**) Generic Keyboard: XkbLayout: "no"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) RADEON(0): [RESUME] Attempting to re-init Radeon hardware.
(II) RADEON(0): [agp] Mode 0x0f000207 [AGP 0x1002/0xcbb2; Card 0x1002/0x4337]
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

