---
title: "Enable Wireless option enabled but wireless still not enabled"
date: 2011-07-21
forum: General Help
---

### Post by nikhilkatakam on 2011-07-21
Hi all,
I'm new to ubuntu and linux so this might be a silly question. 
My problem is that I didnt have my wireless drivers when i installed ubuntu so i downloaded and installed them. 
What happens now is that I try to enable my wireless but the option in the drop down menu shows that the "enable wireless" option is checked but i see the "wireless networks" and "wireless is disabled" options which are still greyed out. i can toggle the enable and disable on the wireless in my options but that doesnt reflect.
Also, when i try to turn on and off the wireless switch on my laptop, the light turns blue and red suggesting that the device is working properly.

I did the sudo lshw -C network in the terminal and this is the output i got 

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5b:75:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f4000000-f4003fff ioport:4000(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:54:48:ff
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.56+Intel,02/25/2007,11.1.0.86 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:f4100000-f4101fff


Apparently, doesnt say enabled or disabled or anything.
Please help.

---

### Post by galvatron408 on 2011-07-22
yea, you should probably type /sbin/ifconfig -a 


wlan0     Link encap:Ethernet  HWaddr 00:13:e8:d1:71:cd  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fed1:71cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12490504 (12.4 MB)  TX bytes:1403706 (1.4 MB)

---

### Post by grahammechanical on 2011-07-22
Is Enable Networking checked? We need both Enable Networking and Enable Wireless to be checked for wireless to work. With just Enable Networking checked we get a wired (ethernet) connection. But if Enable Networking is not checked then we do not get either wired or wireless networking.

Do you see your wireless network/modem in that list? Have you tried clicking on one of the networks.

Regards.

---

