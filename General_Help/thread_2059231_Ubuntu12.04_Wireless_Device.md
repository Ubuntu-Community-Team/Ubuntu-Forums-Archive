---
title: "Ubuntu12.04 Wireless Device"
date: 2012-09-17
forum: General Help
---

### Post by mamo04120 on 2012-09-17
Hi every one.
I was using Ubuntu 12.04 for a while. And something happened and system went very very slow. I re-installed Ubuntu and used that for two days. Then my Wireless Device gone. No in additional drives no in lspci. My WiFi button must have a blue light when it working. But now It's just yellow (Not working) and I can't make it work with hittin it. I have dual boot and Device working well in MS-Windows. Re-installed system again and now it happened again. What is problem?

Here my lspci output:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV516 [Mobility Radeon X1350]

Sorry for bad English.

---

### Post by ajgreeny on 2012-09-17
Can we see the output of ```
sudo lshw -c network
``` to see if that finds your wlan card.
lspci does not see any wireless network card at the moment, which seems odd, if there really is one.  Is your OS still the same version of ubuntu as the one where wireless worked?

---

### Post by mamo04120 on 2012-09-19
> **ajgreeny said:**
> Can we see the output of ```
sudo lshw -c network
``` to see if that finds your wlan card.
lspci does not see any wireless network card at the moment, which seems odd, if there really is one.  Is your OS still the same version of ubuntu as the one where wireless worked?

Here the output.

>  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:4b:6c:f5:2d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-2 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:dc500000-dc51ffff memory:dc520000-dc520fff ioport:5000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:d3:cd:8f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-30-generic-pae firmware=15.32.2.9 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:dc000000-dc000fff


At last I tried with different user to be sure it's not about user configuration files. Nothing changed. Still not working.

---

### Post by mamo04120 on 2012-09-19
OMG. Just two minute ago I had some updates and tried my chance with logout/login. It's works. I'm happy again. (:

How can I find what changed in last system update?

---

### Post by newb85 on 2012-09-19
Software Center has a History feature where you should be able to see all changes made to your system on a given day.

---

