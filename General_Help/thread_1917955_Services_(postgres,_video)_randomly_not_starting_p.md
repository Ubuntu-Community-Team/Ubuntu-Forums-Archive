---
title: "Services (postgres, video) randomly not starting properly after reboot"
date: 2012-01-31
forum: General Help
---

### Post by mzzl on 2012-01-31
Hi everyone, 

Ever since I did a clean install of 11.10, I've had the following problem:

About once every half dozen reboots, the display doesn't seem to start properly. The monitor can't find a signal and drops to sleep. This is not just in X, but in the contole (CTRL-ALT-F1-6) as well. The system is otherwise normally responsive. It accepts network connections and input from the keyboard. When it fails, it often fails in clusters, meaning I have to reboot a few times to get it working. 

About 4 out of 5 reboots, postgres doesn't accept TCP/IP connections. It seems to start up properly, but without the -i option. When i restart postgres manually after booting, it invariably works properly

If it never worked, I could understand that, but this randomness is a little strange. Could anyone here give me some hints on how to trouble shoot this?

# uname -a 
Linux thingie 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
# /usr/lib/postgresql/9.1/bin/postgres --version
postgres (PostgreSQL) 9.1.2
# hwinfo --monitor
> hal.1: read hal dataprocess 17180: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
# hwinfo --framebuffer                      
> hal.1: read hal dataprocess 17185: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.5dHCGM_Ucd6
  Hardware Class: framebuffer
  Model: "Intel(r)Q33/Q35/G33 Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r)Q33/Q35/G33 Graphics Controller"
  SubVendor: "Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 960 kB
  Memory Range: 0xd0000000-0xd07effff (rw)
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by johnfp on 2012-02-21
I have the same error message: libhal.c 3483 Error unsubscribing to signals 


I am running Lubuntu on a Dell Inspiron 510m, having used the recently abandoned LTS version of Ubuntu for a long time.

My main porblem with it is the communicaton with my pop and smtp servers which usually get 'connection timed out',  But SOMETIMES  they work correctly, and the settigns are the same as with the earlier Ubuntu version.
Can this be connected?

Here is what I get

#uname -a

Linux john-study 2.6.38-13-generic #55-Ubuntu SMP Tue Jan 24 14:27:59 UTC 2012 i686 i686 i386 GNU/Linux

#hwinfo --wlan

process 2327: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
17: PCI 103.0: 0282 WLAN controller
  [Created at pci.318]
  Unique ID: JNkJ.C8kmJvRynV3
  Parent ID: 6NW+.+ISWpD3pbdC
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:01:03.0
  SysFS BusID: 0000:01:03.0
  Hardware Class: network
  Model: "Intel Dell Latitude D600"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4220 "PRO/Wireless 2200BG [Calexico2] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x2722 "Dell Latitude D600"
  Revision: 0x05
  Driver: "ipw2200"
  Driver Modules: "ipw2200"
  Device File: eth1
  Features: WLAN
  Memory Range: 0xfcffe000-0xfcffefff (rw,non-prefetchable)
  IRQ: 5 (no events)
  HW Address: 00:0e:35:74:02:2c
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN bitrates: 1 2 5.5 11 6 9 12 18 24 36 48 54
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Requires: ipw-firmware
  Module Alias: "pci:v00008086d00004220sv00008086sd00002722bc02sc80i00"
  Driver Info #0:
    Driver Status: ipw2200 is active
    Driver Activation Cmd: "modprobe ipw2200"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

---

