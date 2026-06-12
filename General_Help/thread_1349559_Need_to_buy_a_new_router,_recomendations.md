---
title: "Need to buy a new router, recomendations?"
date: 2009-12-08
forum: General Help
---

### Post by cptrohn on 2009-12-08
Well my little old cheap $20  Belkin died last night, and I also need to get one that works well with ipv6 anyway...... So what routers have you bought recently for a good price, that also support ipv6?

Am thinking of getting one of the linksys routers that will support ddwrt fairly easily too.

---

### Post by Mighty_Joe on 2009-12-08
> **cptrohn said:**
> Am thinking of getting one of the linksys routers that will support ddwrt fairly easily too.

The complete list of dd-wrt supported routers is [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices") and the recommended models are [here]("http://www.dd-wrt.com/wiki/index.php/Index:FAQ#Which_router_should_I_buy.3F").  I've got a [WRT54GL]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190") (running [Tomato]("http://www.polarcloud.com/tomato"))and it works fine.

---

### Post by Commander_Keen on 2009-12-08
go with Linksys.

---

### Post by sabre2th on 2009-12-08
I couldn't agree more on the WRT54GL.  Mine's run flawlessly since I bought it, no questions asked.  I'm also in the process of getting a couple of friends set up with these.  The only reason I see to go with something else is if you're set on getting an N router.

The Newegg page really says it all... 30x winner of customer choice award.

---

### Post by Marvin666 on 2009-12-08
My routers are netgear wgr614, and linksys wrt54gs. I perfer the linksys one.

---

### Post by lisati on 2009-12-08
I use a Thomson 585 router/ADSL2+ modem (a "freebie" from my ISP, replacing its predecessor, a D-link 502, also a "freebi" from my ISP) and a Netgear WGR614V7 (purchased when I was using the D-link modem). The Thomson one is a bit quirky at times but works. No major hassles with the Netgear router.

---

### Post by Snow986 on 2009-12-08
Cant go wrong with D-link or Linksys.

---

### Post by whoop on 2009-12-08
All the linksys routers I owned went totally berserk with torrent traffic with a lot of seeds and peers...

---

### Post by Mighty_Joe on 2009-12-10
> **whoop said:**
> All the linksys routers I owned went totally berserk with torrent traffic with a lot of seeds and peers...

There's a [known problem]("http://www.p2pforums.com/viewtopic.php?f=9&t=20895") with some Linksys routers where they hold on to closed connections for an absurd amount of time.  The third-party firmware upgrades like DD-WRT and Tomato fix this problem.
A power surge took out my Linksys yesterday. I'm going to give the [Buffalo WHR-HP-G54]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833162134") a try.  It supposedly has a speed and range advantage over the WRT54 and is just as compatible with third-party firmware.

---

### Post by sabre2th on 2009-12-10
> **Mighty_Joe said:**
> There's a [known problem]("http://www.p2pforums.com/viewtopic.php?f=9&t=20895") with some Linksys routers where they hold on to closed connections for an absurd amount of time.  The third-party firmware upgrades like DD-WRT and Tomato fix this problem.
A power surge took out my Linksys yesterday. I'm going to give the [Buffalo WHR-HP-G54]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833162134") a try.  It supposedly has a speed and range advantage over the WRT54 and is just as compatible with third-party firmware.
I've never had any issues with my routers, with or without torrents.  Does it require a certain (obscene?) amount of traffic before it becomes apparent?

---

### Post by friskypiro on 2009-12-10
I use an old linksys G and wow DD-WRT is sweet... I have been looking around and upgradeing old routers that people think are kaput and making them live again!!:twisted:

---

### Post by joes7 on 2009-12-10
> **Mighty_Joe said:**
> The complete list of dd-wrt supported routers is [here]("http://www.dd-wrt.com/wiki/index.php/Supported_Devices") and the recommended models are [here]("http://www.dd-wrt.com/wiki/index.php/Index:FAQ#Which_router_should_I_buy.3F").  I've got a [WRT54GL]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190") (running [Tomato]("http://www.polarcloud.com/tomato"))and it works fine.

WRT54GL is the best router ever. You can find out more at LinkSys' official website.

---

### Post by Mighty_Joe on 2009-12-11
> **sabre2th said:**
> I've never had any issues with my routers, with or without torrents.  Does it require a certain (obscene?) amount of traffic before it becomes apparent?

I have not experienced this problem either. I know about it only from reading the documentation of DD-WRT.  Since we're talking a Linux variant here, presumably it would have 65,000 available ports (minus the 1024 reserved ports).  The timeout is supposedly 5 days, so one would need to figure out what kind of traffic would use over 65,000 connections in less than 5 days.  Obviously, the more traffic, the sooner one would run out of connections.

---

