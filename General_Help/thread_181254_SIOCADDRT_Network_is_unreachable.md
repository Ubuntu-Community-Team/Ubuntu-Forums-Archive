---
title: "SIOCADDRT: Network is unreachable"
date: 2006-05-23
forum: General Help
---

### Post by harty83 on 2006-05-23
To begin with, my wireless card works on most networks.  It works fine at home, work, Barnes and Noble, and other places.  However, there are two coffee shops that I have found that I cannot get a connection.  I will be assigned an IP address from their routers, but I cannot access the internet.  I tired ifup/down and network manger.  The only clue I get is when I use ifup I get:

```
alan@hartyslaptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:90:96:f2:d8:75
Sending on   LPF/eth1/00:90:96:f2:d8:75
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.100
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.100
SIOCADDRT: Network is unreachable
bound to 192.168.1.47 -- renewal in 17256 seconds.
```

I got fed up with trying to figure it out, hibernated my laptop, went home, and bam I can connect at home no problem.  What is it about these two coffee shops wireless internets that causes me not to be able to surf the web when windows users right next to me are surfing to their heart's content?

Here are a couple commands I thought to get while I was at one of the shops:
```
alan@hartyslaptop:~$ sudo iwlist scan
eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:18:EB:88
                    ESSID:"TheCoffeeMill"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-161 dBm
                    Extra: Last beacon: 161ms ago
          Cell 02 - Address: 00:14:BF:03:39:D5
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-184 dBm
                    Extra: Last beacon: 547ms ago
```
```
alan@hartyslaptop:~$ sudo iwconfig
eth1      IEEE 802.11b/g  ESSID:"TheCoffeeMill"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:0C:41:18:EB:88
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level=3/3  Noise level=192/100
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I did not think to ifconfig.  If I go back in the next couple of days, I will make sure I get that too and post it.

Thanks ahead of time!
Alan

---

### Post by harty83 on 2006-05-24
Here is ifconfig:
```

alan@hartyslaptop:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:96:F2:D8:75
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fef2:d875/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:331 overruns:0 frame:0
          TX packets:179 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:926 (926.0 b)  TX bytes:9234 (9.0 KiB)
          Interrupt:193 Base address:0x8000

```

I want to emphasize that my card works fine and that the shops have open systems that are not filtered by mac addresses or passworded.  Thanks.

---

