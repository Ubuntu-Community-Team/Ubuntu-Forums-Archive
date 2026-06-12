---
title: "VPN issues"
date: 2009-11-25
forum: General Help
---

### Post by Ducatiboy Stu on 2009-11-25
Hardy ( 8.04 )

For some reason when I start my VPN it seems to dissapear on  me when I do " ifconfig "  ppp0 just dissapears after a few seconds. I have tried various options in Firestarter but I always get the same result
I can go into windows and set up my VPN/RDP session easly on the same router, but not in Ubuntu. Network manager shows a little VPN icon, and I have to disconnect the VPN to use the net normally....
Anyone got any ideas..:-(

```
ncts@ncts:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:a3:87:4b  
          inet addr:192.168.1.100  Bcast:192.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3034680 (2.8 MB)  TX bytes:1046222 (1021.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54077 (52.8 KB)  TX bytes:54077 (52.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.50.203  P-t-P:192.168.50.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:102 (102.0 B)  TX bytes:96 (96.0 B)

ncts@ncts:~$ 

```
Then this immediatly after....
```
ncts@ncts:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:a3:87:4b  
          inet addr:192.168.1.100  Bcast:192.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3043116 (2.9 MB)  TX bytes:1047192 (1022.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54409 (53.1 KB)  TX bytes:54409 (53.1 KB)

ncts@ncts:~$ 
```

---

### Post by Ducatiboy Stu on 2009-11-27
:neutral:

---

