---
title: "ubuntu 10.10 intel pro wireless 2200 problem / tried solutions but nothing."
date: 2011-03-18
forum: General Help
---

### Post by pigimon on 2011-03-18
hi i have fujitsu-siemens amilo m7440 and the wireles2200 adapter but it doesn't seem to work... the drivers that i found in some posts (on sourceforge) are no longer available cause it says that it comes with new kernels... so i did some stuff like 

iwconfig :
pigimon@pigimon-AMILO-M-Series:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



also did
ifconfig :

pigimon@pigimon-AMILO-M-Series:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:ca:d1:16:b7  
          inet addr:192.168.178.41  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fed1:16b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2784960 (2.7 MB)  TX bytes:542401 (542.4 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8064 (8.0 KB)  TX bytes:8064 (8.0 KB)


and at last 
sudo lshw -C network:
pigimon@pigimon-AMILO-M-Series:~/Desktop$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:23:0a:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:b0108000-b0108fff
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:06:09.0
       logical name: eth0
       version: 01
       serial: 00:40:ca:d1:16:b7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.178.41 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:10 memory:b0106000-b0107fff memory:64000000-6400ffff




so is it a button problem? a driver problem? i really need it to get fixed :S thanks in advance. :)

---

### Post by grahammechanical on 2011-03-18
When you left click the wireless icon do you see any wireless networks in the list? When you right click the icon is there a tick mark against Enable Networking and Enable Wireless? Try clicking to remove the tick mark against Enable Networking and then clicking it again. This might stimulate the wireless adapter into scanning for networks. Also switching the modem/router off and then on will cuase the modem to broadcast a signal that might be picked up by the wireless adapter.

The command sudo ifconfig wlan0 up is also useful. So, is posting a problem like this one in the Networking and wireless part of the forum. You will get help quicker. You will see the advice given to others who are have the same problem.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

