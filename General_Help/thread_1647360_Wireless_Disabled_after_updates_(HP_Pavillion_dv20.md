---
title: "Wireless Disabled after updates (HP Pavillion dv2000)"
date: 2010-12-17
forum: General Help
---

### Post by bienpo on 2010-12-17
Help.

My wireless internet was disabled after doing the updates. The Wirelss LED remains orange all the time, normally it turns blue when enabled.

I tried all sorts of things from other forum. But no luck my wifi still don't work.

Below are the info I've got after running some scripts.

> *-network DISABLED  
                 description: Wireless interface  
                 product: PRO/Wireless 3945ABG [Golan] Network Connection  
                 vendor: Intel Corporation  
                 physical id: 0  
                 bus info: pci@0000:07:00.0  
                 logical name: wlan0  
                 version: 02  
                 serial: 00:1f:3c:82:69:f7  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
                 configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-23-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11abg  
                  resources: irq:47 memory:f4300000-f4300fff  
                  > lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11abg  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
            Power Management:off  
 >                        00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)  
 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)  
 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)  
 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)  
 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)  
 00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)  
 00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)  
 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)  
 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)  
 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)  
 **05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14) ** 
 **07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) ** 
 08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)  
 08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)  
 08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)  
  08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)  
 

---

### Post by bienpo on 2010-12-17
Problem solved.

This script works for me.

sudo rfkill unblock wifi

---

