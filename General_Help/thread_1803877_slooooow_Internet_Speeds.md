---
title: "slooooow Internet Speeds"
date: 2011-07-14
forum: General Help
---

### Post by terrykiwi83 on 2011-07-14
Well basically my internet has been fast, responsive and great on Ubuntu 11.04 x64 Kernel 2.6.38.8 but since upgrading to kernel 2.6.39.3 candela my internet has been having some issues.

On Chrome when I type a URL in and hit Go it sits on 'Sending Request' for about 10 seconds before slowly displaying the website, I have tried lots of different sites and they are all the same.

```

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 68:7F:74:DC:4F:E9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:on**
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:59   Missed beacon:0

```

Do you think it could be because power management is on, I have heard this before and am sure I disabled this on my previous kernel? If so I have no forgot how to disable it.

```

wlan0     Link encap:Ethernet  HWaddr 00:21:27:ce:a6:05  
          inet addr:192.168.1.200  Bcast:192.168.1.200  Mask:255.255.255.255
          inet6 addr: fe80::221:27ff:fece:a605/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2067008 (2.0 MB)  TX bytes:566642 (566.6 KB)

```

```


*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:21:27:ce:a6:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.39.3-candela firmware=1.7 ip=192.168.1.200 multicast=yes wireless=IEEE 802.11bg

```

Any suggestions for optimizing the connection?

---

### Post by terrykiwi83 on 2011-07-14
fixed it myself as usual :)

---

### Post by Xruptor on 2011-07-16
;) would be nice if you listed how you fixed it before you mark it as solved.  That way other people may be able to fix the problem with your solution.  Sorta silly to mark it solved and not provide any details on how you fixed it.  Just a tip to help other people on Ubuntu.

---

