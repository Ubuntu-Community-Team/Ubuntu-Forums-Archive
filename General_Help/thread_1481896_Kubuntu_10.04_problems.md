---
title: "Kubuntu 10.04 problems"
date: 2010-05-13
forum: General Help
---

### Post by elquin on 2010-05-13
Hi, all
I just installed Kubuntu 10.04 on my old desktop and using dual boot with WinXP. but it has several problems.

1. Display setting is always initialize when reboot or restart the system.

2. The sound works only on effect sound. I cannot hear any sound when running youtube.

3. Fan doesn't work properly. Only working is CPU fan.

Here's my information as;
---------------------------------
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
---------------------------------------------------
$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.14 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.22 V  (min =  +2.97 V, max =  +3.63 V)                                                                                                                      
 +5 Voltage:        +4.94 V  (min =  +4.50 V, max =  +5.50 V)                                                                                                                      
 +12 Voltage:      +12.21 V  (min = +10.20 V, max = +13.80 V)                                                                                                                      
CPU FAN Speed:     1147 RPM  (min =  600 RPM)                                                                                                                                      
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)                                                                                                                                      
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =  600 RPM)
CPU Temperature:    +32.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +31.0°C  (high = +45.0°C, crit = +95.0°C)  
----------------------------------------

Any kinds of comments or advice will be welcomed.
If any furthur needed, please let me know.
Thank you.

---

### Post by bilol on 2010-05-13
Hi,
I would prefer light-weight environment instead of kde in old desktops.

---

