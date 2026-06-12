---
title: "Ubuntu don't wan't to connect my adhoc"
date: 2011-01-21
forum: General Help
---

### Post by erefere on 2011-01-21
Hello i am user of ubuntu 10.10 my laptop is Acer 3620 and wireless card is ```
6:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```i've installed drivers from "Additional Drivers" named "Broadcom B43 wireless driver" and ubuntu is seeing my adhoc but when i wan to connect after while i've got this ```
http://img263.imageshack.us/img263/3583/screenshot3qf.jpg

```
What should i do now huh?

iwconfig 
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:f3:9e:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:0c:6d:a1  
          inet6 addr: fe80::216:ceff:fe0c:6da1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6091 (6.0 KB)
```
iwlista scan
```
wlan0     Scan completed :
          Cell 01 - Address: 02:1E:64:00:0C:31
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"sadsadsa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000002c648d657
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00087361647361647361
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010B
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C
```

---

### Post by spiky001 on 2011-01-21
Can you see yor network in network manager?

---

### Post by erefere on 2011-01-22
yes i can see it. I have the same problem on 10.04

---

