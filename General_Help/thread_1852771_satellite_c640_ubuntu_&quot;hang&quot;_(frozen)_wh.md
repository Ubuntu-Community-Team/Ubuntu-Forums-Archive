---
title: "satellite c640: ubuntu &quot;hang&quot; (frozen) when booting without an internet connection"
date: 2011-09-30
forum: General Help
---

### Post by zhu1 on 2011-09-30
I have installed ubuntu 11.04-desktop-amd64 in laptopSatellite c640. originally there were no problems during install. even all the driver has also been detected properly. with an internet connection through lan all fine, but after the restart and then boot with no internet connection ........ when the gdm login is always "hang" (frozen ).......... : (

for the record: I use lan to connect to the internet.

**$ nm-tool**

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        00:26:6C:BE:41:E6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             50.23.239.24
    DNS:             208.67.222.222


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        68:A3:C4:AA:A9:31

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

**$ lshw**
 description: Computer  
 width: 64 bits  
 capabilities: vsyscall64 vsyscall32  
 *-core  
 description: Motherboard  
 physical id: 0  
 *-memory  
 description: System memory  
 physical id: 0  
 size: 1603MiB  
 *-cpu  
 product: AMD E-350 Processor  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 1  
 bus info: cpu@0  
 size: 800MHz  
 capacity: 800MHz  
 width: 64 bits  
 capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt npt lbrv svm_lock nrip_save pausefilter cpufreq  
 *-pci:0  
 description: Host bridge  
 product: Pavilion DM1Z-3000 Host bridge 
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 100  
 bus info: pci@0000:00:00.0  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 *-display  
 description: VGA compatible controller  
 product: ATI Technologies Inc  
 vendor: ATI Technologies Inc  
 physical id: 1  
 bus info: pci@0000:00:01.0  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 capabilities: vga_controller bus_master cap_list rom  
 configuration: driver=radeon latency=0  
 resources: irq:41 memory:80000000-8fffffff ioport:4000(size=256) memory:90300000-9033ffff  
 *-storage  
 description: SATA controller  
 product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]  
 vendor: ATI Technologies Inc  
 physical id: 11  
 bus info: pci@0000:00:11.0  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: storage ahci_1.0 bus_master cap_list  
 configuration: driver=ahci latency=64  
 resources: irq:19 ioport:4138(size=8) ioport:414c(size=4) ioport:4130(size=8) ioport:4148(size=4) ioport:4110(size=16) memory:9034a000-9034a3ff  
 *-usb:0  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 vendor: ATI Technologies Inc  
 physical id: 12  
 bus info: pci@0000:00:12.0  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ohci bus_master  
 configuration: driver=ohci_hcd latency=64  
 resources: irq:18 memory:90349000-90349fff  
 *-usb:1  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 vendor: ATI Technologies Inc  
 physical id: 12.2  
 bus info: pci@0000:00:12.2  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ehci bus_master cap_list  
 configuration: driver=ehci_hcd latency=64  
 resources: irq:17 memory:90348000-903480ff  
 *-usb:2  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 vendor: ATI Technologies Inc  
 physical id: 13  
 bus info: pci@0000:00:13.0  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ohci bus_master  
 configuration: driver=ohci_hcd latency=64  
 resources: irq:18 memory:90347000-90347fff  
 *-usb:3  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 vendor: ATI Technologies Inc  
 physical id: 13.2  
 bus info: pci@0000:00:13.2  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ehci bus_master cap_list  
 configuration: driver=ehci_hcd latency=64  
 resources: irq:17 memory:90346000-903460ff  
 *-serial  
 description: SMBus  
 product: SBx00 SMBus Controller  
 vendor: ATI Technologies Inc  
 physical id: 14  
 bus info: pci@0000:00:14.0  
 version: 42  
 width: 32 bits  
 clock: 66MHz  
 configuration: driver=piix4_smbus latency=0  
 resources: irq:0  
 *-multimedia  
 description: Audio device  
 product: SBx00 Azalia (Intel HDA)  
 vendor: ATI Technologies Inc  
 physical id: 14.2  
 bus info: pci@0000:00:14.2  
 version: 40  
 width: 64 bits  
 clock: 33MHz  
 capabilities: bus_master cap_list  
 configuration: driver=HDA Intel latency=64  
 resources: irq:16 memory:90340000-90343fff  
 *-isa  
 description: ISA bridge  
 product: SB7x0/SB8x0/SB9x0 LPC host controller  
 vendor: ATI Technologies Inc  
 physical id: 14.3  
 bus info: pci@0000:00:14.3  
 version: 40  
 width: 32 bits  
 clock: 66MHz  
 capabilities: isa bus_master  
 configuration: latency=0  
 *-pci:0  
 description: PCI bridge  
 product: SBx00 PCI to PCI Bridge  
 vendor: ATI Technologies Inc  
 physical id: 14.4  
 bus info: pci@0000:00:14.4  
 version: 40  
 width: 32 bits  
 clock: 66MHz  
 capabilities: pci normal_decode bus_master  
 *-pci:1  
 description: PCI bridge  
 product: ATI Technologies Inc  
 vendor: ATI Technologies Inc  
 physical id: 15  
 bus info: pci@0000:00:15.0  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 capabilities: pci normal_decode bus_master cap_list  
 configuration: driver=pcieport  
 resources: irq:16 ioport:3000(size=4096) memory:90200000-902fffff ioport:90000000(size=1048576)  
 *-network DISABLED  
 description: Wireless interface  
 product: AR9285 Wireless Network Adapter (PCI-Express)  
 vendor: Atheros Communications Inc.  
 physical id: 0  
 bus info: pci@0000:02:00.0  
 logical name: wlan0  
 version: 01  
 serial: 68:a3:c4:aa:a9:31  
 width: 64 bits  
 clock: 33MHz  
 capabilities: bus_master cap_list ethernet physical wireless  
 configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn  
 resources: irq:16 memory:90200000-9020ffff  
 *-pci:2  
 description: PCI bridge  
 product: ATI Technologies Inc  
 vendor: ATI Technologies Inc  
 physical id: 15.1  
 bus info: pci@0000:00:15.1  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 capabilities: pci normal_decode bus_master cap_list  
 configuration: driver=pcieport  
 resources: irq:16 ioport:2000(size=4096) memory:90100000-901fffff  
 *-network  
 description: Ethernet interface  
 product: AR8152 v2.0 Fast Ethernet  
 vendor: Atheros Communications  
 physical id: 0  
 bus info: pci@0000:06:00.0  
 logical name: eth0  
 version: c1  
 serial: 00:26:6c:be:41:e6  
 size: 100Mbit/s  
 capacity: 100Mbit/s  
 width: 64 bits  
 clock: 33MHz  
 capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
 configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 multicast=yes port=twisted pair speed=100Mbit/s  
 resources: irq:40 memory:90100000-9013ffff ioport:2000(size=128)  
 *-usb:4  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 vendor: ATI Technologies Inc  
 physical id: 16  
 bus info: pci@0000:00:16.0  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ohci bus_master  
 configuration: driver=ohci_hcd latency=64  
 resources: irq:18 memory:90345000-90345fff  
 *-usb:5  
 description: USB Controller  
 product: SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 vendor: ATI Technologies Inc  
 physical id: 16.2  
 bus info: pci@0000:00:16.2  
 version: 00  
 width: 32 bits  
 clock: 66MHz  
 capabilities: ehci bus_master cap_list  
 configuration: driver=ehci_hcd latency=64  
 resources: irq:17 memory:90344000-903440ff  
 *-pci:1  
 description: Host bridge  
 product: Family 12h/14h Processor Function 0  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 101  
 bus info: pci@0000:00:18.0  
 version: 43  
 width: 32 bits  
 clock: 33MHz  
 *-pci:2  
 description: Host bridge  
 product: Family 12h/14h Processor Function 1  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 102  
 bus info: pci@0000:00:18.1  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-pci:3  
 description: Host bridge  
 product: Family 12h/14h Processor Function 2  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 103  
 bus info: pci@0000:00:18.2  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-pci:4  
 description: Host bridge  
 product: Family 12h/14h Processor Function 3  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 104  
 bus info: pci@0000:00:18.3  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 configuration: driver=k10temp  
 resources: irq:0  
 *-pci:5  
 description: Host bridge  
 product: Family 12h/14h Processor Function 4  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 105  
 bus info: pci@0000:00:18.4  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-pci:6  
 description: Host bridge  
 product: Family 12h/14h Processor Function 6  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 106  
 bus info: pci@0000:00:18.5  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-pci:7  
 description: Host bridge  
 product: Family 12h/14h Processor Function 5  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 107  
 bus info: pci@0000:00:18.6  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-pci:8  
 description: Host bridge  
 product: Family 12h/14h Processor Function 7  
 vendor: Hynix Semiconductor (Hyundai Electronics)  
 physical id: 108  
 bus info: pci@0000:00:18.7  
 version: 00  
 width: 32 bits  
 clock: 33MHz  
 *-scsi  
 physical id: 1  
 bus info: scsi@3  
 logical name: scsi3  
 capabilities: scsi-host  
 configuration: driver=usb-storage  
 

this is my ***blacklist.conf***
 *# This file lists those modules which we don't want to be loaded by *
 *# alias expansion, usually so some other driver will be loaded for the *
 *# device instead. *
 
 *# evbug is a debug tool that should be loaded explicitly *
 *blacklist evbug *
 
 *# these drivers are very simple, the HID drivers are usually preferred *
 *blacklist usbmouse *
 *blacklist usbkbd *
 
 *# replaced by e100 *
 *blacklist eepro100 *
 
 *# replaced by tulip *
 *blacklist de4x5 *
 
 *# causes no end of confusion by creating unexpected network interfaces *
 *blacklist eth1394 *
 
 *# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much *
 *# hardware on its own (Ubuntu bug #2011, #6810) *
 *blacklist snd_intel8x0m *
 
 *# Conflicts with dvb driver (which is better for handling this device) *
 *blacklist snd_aw2 *
 
 *# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) *
 *blacklist i2c_i801 *
 
 *# replaced by p54pci *
 *blacklist prism54 *
 
 *# replaced by b43 and ssb. *
 *blacklist bcm43xx *
 
 *# most apps now use garmin usb driver directly (Ubuntu: #114565) *
 *blacklist garmin_gps *
 
 *# replaced by asus-laptop (Ubuntu: #184721) *
 *blacklist asus_acpi *
 
 *# low-quality, just noise when being used for sound playback, causes *
 *# hangs at desktop session start (Ubuntu: #246969) *
 *blacklist snd_pcsp *
 
 *# ugly and loud noise, getting on everyone's nerves; this should be done by a *
 *# nice pulseaudio bing (Ubuntu: #77010) *
 *blacklist pcspkr *
 
 *# EDAC driver for amd76x clashes with the agp driver preventing the aperture *
 *# from being initialised (Ubuntu: #297750). Blacklist so that the driver *
 *# continues to build and is installable for the few cases where its *
 *# really needed. *
 *blacklist amd76x_edac*


what's wrong there? please ....... help me ..?:sad:

---

