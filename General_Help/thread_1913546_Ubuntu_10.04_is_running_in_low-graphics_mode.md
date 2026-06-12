---
title: "Ubuntu 10.04 is running in low-graphics mode"
date: 2012-01-22
forum: General Help
---

### Post by NoMansLan333 on 2012-01-22
As the title says, when I boot up I get an error that says "Ubuntu is running low-graphics mode". I don't whats going on and it hasn't been doing this till recently. I inlcuded a snap shot of the screen error I get.

When I look in **/etc/X11/xorg.conf**, it is empty, nothing in there at all.

So I look in xorg.conf.failsafe...

**xorg.conf.failsafe Info**
```
sudo gedit /etc/X11/xorg.conf.failsafe

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

**Video Info**
```
$ lspci -vvv

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0136
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 28
    Region 0: Memory at d4000000 (64-bit, non-prefetchable) [size=1M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 5110 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0136
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at d8400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
```


**Computer Info**
```
$ sudo lshw
 
    description: Computer
    product: Aspire 5315
    vendor: Acer
    version: V1.43
    serial: XXXX
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: cpus=1 uuid=EE743358-F0E8-316B-438C-001B38DC9723
  *-core
       description: Motherboard
       product: Acadia
       vendor: Acer
       physical id: 0
       version: V1.43
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.43 (06/25/2008)
          size: 1MiB
```

---

