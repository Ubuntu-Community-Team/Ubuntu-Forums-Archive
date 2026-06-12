---
title: "eth0 loopback interface dissapeared"
date: 2006-06-16
forum: General Help
---

### Post by ultralame on 2006-06-16
During some installation process, I seem to have lost the loopback interface.
I try to restart networking, and it doesn't help.

Why is it missing?  Looks like there is an entry in the 'interafces' file.

Here's details...
[INDENT]
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.254

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                                                                            [ ok ]

$ sudo /etc/init.d/networking start
 * Configuring network interfaces... 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
[/INDENT]



[INDENT]$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B5:8D:74:F3
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: <MAC ADDRESS>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1076889 (1.0 MiB)  TX bytes:491134 (479.6 KiB)
          Interrupt:201 Base address:0x6000
[/INDENT]

---

### Post by caserio on 2006-06-16
Hi,

Did you try  ping localhost
cat /etc/hosts ?
Special vmware-player config ?
Did you reboot ?

---

### Post by ranf on 2006-06-16
`networking start' complains about: eth1, eth2, ath0 and wlan0. Comment them out first.

Looks like you were playing with WLAN lately.

---

