---
title: "HP Netbook -- no internet"
date: 2010-06-24
forum: General Help
---

### Post by mudeye on 2010-06-24
I have a HP mini 1000 netbook running U10.04 and am not able to get online (I can communicate with this machine via keyboard and flash drive only; there is no ethernet or CD drive).  I tried Ubuntu remix and Moblin with the same results).
 

 It appears that there are three main approaches to the problem: edit current packages with the vi editor; download the needed packages with my desktop and move them to the mini with the Flash drive; or load an earlier version of Ubuntu (i.e., 9.04 or 9.10) onto the mini and hope I then can get online.
 

 I will greatly appreciate pointers and suggestions but note that I will need rather specific directions and steps since I am new to the OS.
 

 Here are what I hope are relevant data:
 	HP Mini 1000
 	Product Number FW376UA#ABA
 	BIOS version F.11
 

 sudo lspci
 

 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller  
 mary@mary-laptop:~$  
 

 sudo iwconfig
 

 lo        no wireless extensions.  
 eth0      no wireless extensions.  
 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
            
 sudo ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:24:81:65:76:94   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:80 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:80 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:6224 (6.2 KB)  TX bytes:6224 (6.2 KB)  
 

 

 sudo lspci -v | less
 

 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
         Subsystem: Hewlett-Packard Company Device 361a  
         Flags: bus master, fast devsel, latency 0  
         Capabilities: [e0] Vendor Specific Information <?>  
         Kernel driver in use: agpgart-intel  
         Kernel modules: intel-agp  
 

 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
         Subsystem: Hewlett-Packard Company Device 361a  
         Flags: bus master, fast devsel, latency 0, IRQ 16  
         Memory at fe980000 (32-bit, non-prefetchable) [size=512K]  
         I/O ports at dc80 [size=8]  
         Memory at d0000000 (32-bit, prefetchable) [size=256M]  
         Memory at fe940000 (32-bit, non-prefetchable) [size=256K]  
         Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
         Capabilities: [d0] Power Management version 2  
         Kernel driver in use: i915  
         Kernel modules: i915  
 

 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML E:  
 

 sudo lsusb
 

 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive  
 Bus 001 Device 003: ID 10f1:1a08   
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by dandnsmith on 2010-06-24
> 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller 

There is an ethernet controller - the alternative is the Broadcom BCM4312 wireless, which is currently giving anothe (dell) user a headache.

I'd go for the ethernet, which is the way I got my internet on a netbook up initially, and then try to sort out the wireless.

If the worst comes to pass, then consider getting hold of a CD device connected via USB - you can boot from those, as well.

---

