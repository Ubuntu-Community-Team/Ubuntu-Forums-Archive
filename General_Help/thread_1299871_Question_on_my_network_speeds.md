---
title: "Question on my network speeds"
date: 2009-10-24
forum: General Help
---

### Post by sports fan Matt on 2009-10-24
*-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:90:9b:87:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=66.169.189.122 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:febfe000-febfefff ioport:e800(size=64)

I realize I have an intel card, but can someone decipher my speed downloading results?  Or do I need to run a speed test? 
Edit: I've just always wanted to know my speeds.

---

### Post by DeMus on 2009-10-24
> **sox fan Matt said:**
> *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:90:9b:87:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=66.169.189.122 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:febfe000-febfefff ioport:e800(size=64)

I realize I have an intel card, but can someone decipher my speed downloading results?  Or do I need to run a speed test? 
Edit: I've just always wanted to know my speeds.

What is connected to your lan card? Is it a router, is it a modem?
When it is a router the speed between router and computer will be maximum 100MB/s.
With a modem it will the maximum speed your Internet Service Provider is giving you.
So, it is difficult to say from here. You have to give some more details.

---

### Post by QLee on 2009-10-24
[QUOTE=sox fan Matt]
I realize I have an intel card, but can someone decipher my speed downloading results?  Or do I need to run a speed test? 
Edit: I've just always wanted to know my speeds.[/QUOTE]

What you have included shows the capabilities of the card, yes, do a speed test to a site somewhere to see what real world speeds your 'Net connection gives. I suggest you try it to two or more sites and try ones that are both close to you and far away (even different times of the day) to get a better idea of what kind of performance you can expect as normal.

---

### Post by sports fan Matt on 2009-10-24
Yep, I've got a router...[[IMG]http://www.speedtest.net/result/601592070.png[/IMG]](http://www.speedtest.net)

From Dallas, Texas..(35 miles away)

From Cincinnati, OH (850 Mi)

[[IMG]http://www.speedtest.net/result/601593382.png[/IMG]](http://www.speedtest.net)

---

### Post by QLee on 2009-10-24
So, you have two sites from different distances giving you speeds in the same ballpark at the current time (on a weekend). You might also try sometime when the rest of the USA is asleep, or during normal business hours, weekdays, sometimes things are faster when most people in an area are asleep sometimes slower when there's lots of 'Net activity and or 'Net routing problems.

The two you have should allow you to compare to what your ISP says they are guaranteeing you.

---

### Post by P4man on 2009-10-24
Your network card can do "100 mbit", which in reality means something around 12 Mega Byte/s in either direction.

Most internet connections are a lot slower than that though, seems you get around 13 Mbit effective download speed (probably 15 Mbit connection) which is quite good, and about 1 Mbit upload, which is also pretty fast in my book.  

Bottom line, you dont need a faster network card, it wont help. If you still think you internet is slow, good luck finding a faster provider.

---

### Post by sports fan Matt on 2009-10-24
Generally speaking, those speeds aren't that bad? (I don't honestly think so)

---

