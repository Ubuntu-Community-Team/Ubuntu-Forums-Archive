---
title: "ntpd doesn't sync"
date: 2009-09-08
forum: General Help
---

### Post by scebert on 2009-09-08
Ntpd has recently stopped syncing my clock. The process is running but it can't connect to any servers. The following is from my log during boot.
```

Sep  8 17:22:18 scebert-laptop ntpd[3715]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Sep  8 17:22:18 scebert-laptop ntpd[3716]: precision = 1.000 usec
Sep  8 17:22:18 scebert-laptop ntpd[3716]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep  8 17:22:18 scebert-laptop ntpd[3716]: Listening on interface #1 wildcard, ::#123 Disabled
Sep  8 17:22:18 scebert-laptop ntpd[3716]: Listening on interface #2 lo, ::1#123 Enabled
Sep  8 17:22:18 scebert-laptop ntpd[3716]: Listening on interface #3 eth1, fe80::21f:e1ff:fe53:8fc0#123 Enabled
Sep  8 17:22:18 scebert-laptop ntpd[3716]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Sep  8 17:22:18 scebert-laptop ntpd[3716]: kernel time sync status 0040
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: host name not found: ntps1-2.uni-erlangen.de
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: couldn't resolve `ntps1-2.uni-erlangen.de', giving up on it
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: host name not found: ntpa2.kph.uni-mainz.de
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: couldn't resolve `ntpa2.kph.uni-mainz.de', giving up on it
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: host name not found: swisstime.ethz.ch
Sep  8 17:22:20 scebert-laptop ntpd_initres[3745]: couldn't resolve `swisstime.ethz.ch', giving up on it
```

It doesn't sync with ntpdate either
```

$ sudo ntpdate swisstime.ethz.ch
 8 Sep 17:40:59 ntpdate[8217]: no server suitable for synchronization found

```
The same thing happens with any server I try. When running ntpdate and not trying to sync it works correctly.

```

$ sudo ntpdate -d swisstime.ethz.ch
 8 Sep 17:47:51 ntpdate[9348]: ntpdate 4.2.4p4@1.1520-o Wed May 13 21:05:44 UTC 2009 (1)
transmit(129.132.2.21)
receive(129.132.2.21)
transmit(129.132.2.21)
receive(129.132.2.21)
transmit(129.132.2.21)
receive(129.132.2.21)
transmit(129.132.2.21)
receive(129.132.2.21)
transmit(129.132.2.21)
server 129.132.2.21, port 123
stratum 2, precision -20, leap 00, trust 000
refid [129.132.2.21], delay 0.03282, dispersion 0.00017
transmitted 4, in filter 4
reference time:    ce50faef.6aa0d455  Tue, Sep  8 2009 17:46:55.416
originate timestamp: ce50fb1a.246754fa  Tue, Sep  8 2009 17:47:38.142
transmit timestamp:  ce50fb27.5b5a5332  Tue, Sep  8 2009 17:47:51.356
filter delay:  0.03342  0.03481  0.03287  0.03282 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -13.2181 -13.2192 -13.2182 -13.2182
         0.000000 0.000000 0.000000 0.000000
delay 0.03282, dispersion 0.00017
offset -13.218257

 8 Sep 17:47:51 ntpdate[9348]: step time server 129.132.2.21 offset -13.218257 sec

```

The offset is the actual offset of my clock from the correct time. 

I moved to a different location and therefore a different network a couple weeks ago, and it was working before that, so it may be related.

---

