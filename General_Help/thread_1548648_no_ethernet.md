---
title: "no ethernet"
date: 2010-08-08
forum: General Help
---

### Post by dovael on 2010-08-08
After using bleachbit on my other computer to "cleanup" unnecessary file, I apparently erased driver for ethernet connection or did something that does not enable me to connect to internet. Below is
**lspci**

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

**ifconfig -a**

eth1      Link encap:Ethernet  HWaddr 00:24:21:5e:75:18  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:26 Base address:0xe000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:102 errors:0 dropped:0 overruns:0 frame:0

          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:11949 (11.9 KB)  TX bytes:11949 (11.9 KB)



vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by DarthScape on 2010-08-08
$ sudo dhclient -r
$ sudo dhclient

---

### Post by dovael on 2010-08-08
Hi Darth. Did as suggested and got

dov@dov-desktop:~$ sudo dhclient -r

[sudo] password for dov: 

Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.

For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)



Listening on LPF/vboxnet0/0a:00:27:00:00:00

Sending on   LPF/vboxnet0/0a:00:27:00:00:00

Listening on LPF/eth1/00:24:21:5e:75:18

Sending on   LPF/eth1/00:24:21:5e:75:18

Sending on   Socket/fallback

dov@dov-desktop:~$ sudo dhclient

Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.

For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)



Listening on LPF/vboxnet0/0a:00:27:00:00:00

Sending on   LPF/vboxnet0/0a:00:27:00:00:00

Listening on LPF/eth1/00:24:21:5e:75:18

Sending on   LPF/eth1/00:24:21:5e:75:18

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17

DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 21

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20

DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 12

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14

DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 12

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3

No DHCPOFFERS received.

No working leases in persistent database - sleeping.


What next?

---

