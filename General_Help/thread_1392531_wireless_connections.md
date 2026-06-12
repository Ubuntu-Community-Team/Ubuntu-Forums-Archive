---
title: "wireless connections"
date: 2010-01-28
forum: General Help
---

### Post by dato1989 on 2010-01-28
hello   everybody i have   dual bootings win7/ubuntu 9.10 in windows  there is not any problem   with wireless   problems is in ubuntu 9.10 i have       Tenda wireless connections 
  so what i need to setup tenda wireless connections in ubuntu?please help me if you need any informations   tell me da i will give  you
thanks

---

### Post by amsterdamharu on 2010-01-28
If you click on the network applet (computer screens next to the speaker (volume control)) do you have wireless network there?

From there you could basically use the gui to set up the wireless but usually it is auto detected on startup so maybe your wireless adapter is not installed. You can check here for more info:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Card](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Card)


Is Tenda your wireless card in the computer or your router?

---

### Post by dato1989 on 2010-01-28
> **amsterdamharu said:**
> If you click on the network applet (computer screens next to the speaker (volume control)) do you have wireless network there?

From there you could basically use the gui to set up the wireless but usually it is auto detected on startup so maybe your wireless adapter is not installed. You can check here for more info:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Card]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#By%20Card")


Is Tenda your wireless card in the computer or your router?
thanks for reply no maybe no yes here is wireless network but it is disconected what i should do?
here is output
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at e4400000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0
    Memory at e4500000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at e4600000 (32-bit, non-prefetchable) [size=128K]
    Memory at e4620000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4020 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 4040 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at e4621000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e4624000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: e4000000-e40fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=28, subordinate=28, sec-latency=0
    I/O behind bridge: 00002000-00003fff
    Memory behind bridge: e0000000-e3ffffff
    Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 4060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 4080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 40a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at e4628000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 80 [Master])
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 40c0 [size=16]
    I/O ports at 40d0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
    Subsystem: Hewlett-Packard Company Device 1371
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at e4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

---

### Post by dato1989 on 2010-01-28
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.
ifconfig
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:9c:2e:1a  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe9c:2e1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:20216097 (20.2 MB)  TX bytes:3932990 (3.9 MB)
          Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58386 (58.3 KB)  TX bytes:58386 (58.3 KB)



any idea?

---

### Post by anaconda on 2010-01-28
these might be of help:

[http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/](http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/)
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I think I have the same broadcom chip on my home machine... And it worked out of the box in 9.04, but in 9.10 it needed a small fix, which I did months ago..

Just follwo the instructions, and reboot, and then networkmanager should show all available wireless networks.....

---

### Post by dato1989 on 2010-01-28
> **anaconda said:**
> these might be of help:

[http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/](http://jetpackweb.com/blog/2009/10/29/ubuntu-9-10-karmic-koala-and-broadcom-bcm4312/)
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I think I have the same broadcom chip on my home machine... And it worked out of the box in 9.04, but in 9.10 it needed a small fix, which I did months ago..

Just follwo the instructions, and reboot, and then networkmanager should show all available wireless networks.....
yes but when i click activated it starts install drivers  but it failed and write to me  look  at the detailed informations in /var/log/jockey.log file 
what i should do?

---

