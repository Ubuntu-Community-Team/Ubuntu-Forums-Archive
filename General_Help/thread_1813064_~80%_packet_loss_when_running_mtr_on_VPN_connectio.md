---
title: "~80% packet loss when running mtr on VPN connection"
date: 2011-07-27
forum: General Help
---

### Post by 98174 on 2011-07-27
```
admin@DELL ~ $  > mtr -r -c 25 www.google.com
HOST: DELL                        Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- ???                       100.0    25    0.0   0.0   0.0   0.0   0.0
  2.|-- uiuc-vpn3-net.gw.uiuc.edu 52.0%    25  1484. 1361. 489.6 1544. 315.0
  3.|-- 172.20.20.237             56.0%    25  1490. 1392. 495.0 1572. 321.9
  4.|-- 172.20.20.5               80.0%    25  1520. 1281. 493.2 1569. 452.9
  5.|-- t-exit1.gw.uiuc.edu       80.0%    25  1526. 1350. 693.0 1537. 368.7
  6.|-- t-fw1.gw.uiuc.edu         72.0%    25  1501. 1395. 696.8 1550. 308.9
  7.|-- t-exite1.gw.uiuc.edu      64.0%    25  1512. 1431. 696.7 1540. 275.9
  8.|-- t-exite2.gw.uiuc.edu      76.0%    25  1541. 1430. 904.7 1542. 257.9
  9.|-- t-dmzb.gw.uiuc.edu        84.0%    25  1554. 1378. 904.5 1554. 316.7
 10.|-- ur2rtr-uiuc.ex.ui-iccn.or 68.0%    25  1514. 1445. 900.3 1563. 221.3
 11.|-- t-710rtr.ix.ui-iccn.org   79.2%    24  1544. 1542. 1525. 1558.  14.2
 12.|-- i2-cps.ex.ui-iccn.org     75.0%    24  1558. 1555. 1527. 1566.  14.4
 13.|-- 74.125.48.105             79.2%    24  1537. 1538. 1513. 1568.  22.5
 14.|-- 72.14.236.178             79.2%    24  1532. 1540. 1523. 1558.  15.5
 15.|-- 209.85.250.30             75.0%    24  1565. 1545. 1514. 1565.  20.2
 16.|-- 74.125.225.82             87.5%    24  1572. 1553. 1517. 1572.  31.8
```

I manually configured my VPN connection in /etc/ppp/peers, since the VPN manager appeared to be 'buggy' (i.e. would become unresponsive when I tried to set up a VPN over a PPPoE connection).

I adjusted my routes to use my ppp1 (VPN) connection for almost all browsing.  Have I misconfigured something...?

Some more background information: My VPN is about halfway around the world from where I am / my PPPoE connection.  I've already changed my DNS servers in /etc/resolv.conf to Google's 8.8.8.8.

I get around 2 kBps on Ubuntu and 50 kBps on Windows using the same VPN. =/

---

### Post by 98174 on 2011-07-28
Bump.

Any hypotheses as to the cause?

---

### Post by varunendra on 2011-07-29
I have no experience with VPN in Ubuntu so can't help with that, and that's why I was waiting for someone else to step in. But now that two days have passed and no one seems interested, I think it's not bad if I make an attempt.

Are you sure the problem is just with the VPN and not with normal browsing? Because I've seen some buggy drivers causing packet drops, and if that is the case then fixing the driver may fix the VPN issue too.

If you think there's a possibility of that, please post the outputs of:
```
ifconfig
```
(after browsing a few min.)
and,
```
sudo lshw -C network
```

---

### Post by 98174 on 2011-07-29
Normal browsing is fine.  I normally connect to the internet via  PPPoE connection configured via pppoeconf.  With this, I get about 250 kBps and 0% packet loss.

I'll post the results of what you've asked the next time I have access to my Ubuntu machine.

---

### Post by Azdour on 2011-07-29
Hi,

I was playing with mtr the other day and I was experiencing similar packet loss even though my Internet and VPN connection runs fine. For me it was explained on this site:

From: [http://serverfault.com/questions/97277/high-percentage-of-lost-packets-tcp-icmp-mtr-complain-to-isp](http://serverfault.com/questions/97277/high-percentage-of-lost-packets-tcp-icmp-mtr-complain-to-isp)

"Many routers are typically programmed to give lower priority to ICMP packets so they aren't "wasting" processing power over "real" traffic. Just because you see a hop with high loss doesn't mean it's slowing down "real" traffic; it may only be throwing away ICMP. That's not necessarily good because it might mean the router is too busy, but it's not guaranteed.

The router may also be programmed to limit the number of responses it sends to ICMP packets in an effort to mitigate DoS attacks."

---

### Post by 98174 on 2011-07-29
Hmm, from my understanding of the link you posted: the router may be too busy to handle my traffic.

I don't think this is a likely scenario, however, as I am getting roughly 80% packet loss across all hops, not just a small set of 3 or 4.  Also, my VPN browsing is severely slow right now; as I mentioned previously, I am getting at most 2 kBps, which is far slower than even the internet I had 10 years ago.  

Then again, on Windows (which is doing the same hops on the same routers), I get 0% packet loss and 50 kBps.  Something's not adding up here.

---

### Post by Sergius14 on 2011-07-29
Maybe is a buggy driver or vpn software for your specific hardware/software combination.

What type of VPN are we talking about? PPTP, L2TP, IPSec? What is the other Endpoint?


If you are using IPSec, give a try to other ESP/AH combinations and see whats happens.

---

### Post by 98174 on 2011-07-29
It's a PPTP VPN.

I'm not quite sure what you mean by other endpoint; can you clarify?

---

### Post by Sergius14 on 2011-07-29
Yes, I want to know if PPTP server are a Linksys router, a Windows Server, etc. 

Can you try to change to IPSec? They are a little difficult to setup at first, but then they are pretty standard and far more secure...

---

### Post by 98174 on 2011-07-30
Unfortunately, the VPN server is not under my control, so I don't think changing the authentication would be an option.  I also don't know what architecture the VPN is hosted on.

---

### Post by dcstar on 2011-07-30
> **98174 said:**
> Unfortunately, the VPN server is not under my control, so I don't think changing the authentication would be an option.  I also don't know what architecture the VPN is hosted on.

Reduce the MTU of your VPN connection and see what happens.

---

### Post by 98174 on 2011-07-31
I have tried as low as 1412, without much result.  Will going lower or to a certain magic number help?

---

### Post by zero2xiii on 2011-07-31
Have a look here, 

Seems like you can down into the hundreds, maybe even check your windows's MTU and carry that over to your linux install:

[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

---

