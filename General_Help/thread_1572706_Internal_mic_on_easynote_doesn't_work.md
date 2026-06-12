---
title: "Internal mic on easynote doesn't work"
date: 2010-09-11
forum: General Help
---

### Post by gullge on 2010-09-11
The sound is working fine, but i can't record with the internal  microphone. i check the levels in alsamixer and everything is in 100%.    Please help me !  :(
 my laptop model is : Packardbell Easynote TR-87


 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
**  $ dpkg -l alsa-***


 Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nombre         Versión       Descripción
+++-==============-==============-============================================
ii  alsa-base      1.0.23+dfsg-1u ALSA driver configuration files
un  alsa-oss       <ninguna>      (no hay ninguna descripción disponible)
ii  alsa-utils     1.0.23-2ubuntu Utilities for configuring and using ALSA


 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
     

   **  $ lspci -nn | grep Audio**
 

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)


 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
     

**     $ cat /proc/asound/card0/codec#0 | grep Codec**

Codec: VIA VT1702


 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      

  **   $ hwinfo --sound**


 > hal.1: read hal dataprocess 2005: arguments to dbus_move_error()  were incorrect, assertion "(dest) == NULL || !dbus_error_is_set  ((dest))" failed in file dbus-errors.c line 278.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
13: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: u1Nb.qtgE2CKW7I2
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x020a
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf0700000-0xf0703fff (rw,non-prefetchable)
  IRQ: 45 (4417 events)
  Module Alias: "pci:v00008086d0000293Esv00001025sd0000020Abc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by cespinal on 2010-09-13
useless mic epidemic.... 
+1 on this

---

