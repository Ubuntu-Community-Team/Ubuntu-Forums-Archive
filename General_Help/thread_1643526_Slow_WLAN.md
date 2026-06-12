---
title: "Slow WLAN"
date: 2010-12-12
forum: General Help
---

### Post by mr_luksom on 2010-12-12
I've noticed that file transfers (via NFS) and streaming (MythTV) are painfully slow on WLAN (~1MB/s) for Ubuntu clients. This is a bit strange, as there is an 802.11n connection, and my windows machine can get around 10-11MB/s.

I have tried disabling security on the AP, no change in transfer rate. I've also tried different modes on the router (G, N, B/G/N). Setting the rate with iwconfig does nothing, as its autoconfigured link speed is 150Mbit/s.

Any pointers on what to look for?

lshw -c network

```
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:e0:4c:01:0a:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.1.1.5 multicast=yes wireless=IEEE 802.11bgn

```

iwconfig

```


wlan0     IEEE 802.11bgn  ESSID:"Kas II"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 94:44:52:4E:06:12   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/100  Signal level=-74 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

route -n
```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 wlan0

```

---

