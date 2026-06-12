---
title: "Asus usb-n13"
date: 2010-12-16
forum: General Help
---

### Post by rhe_green_bastard on 2010-12-16
I'm a newbie here, on both the forums and with Linux. I'm using the Mint distro, and I'm having a problem with my ASUS USB-N13 wireless-n receiver. After much fidgeting with the stock Linux drivers, and with ndiswrapper, I used the solution posted here: [http://www.pclinuxos.com/forum/index.php/topic,76312.0.html](http://www.pclinuxos.com/forum/index.php/topic,76312.0.html)

It worked like a dream after that. Or so I thought. I soon noticed, having bought a new 802.11n router (a D-Link - DIR-615) that my USB-N13 (which is N-capable) was stuck at 54 mbps, while the laptops were running at a cool 130-135 mbps. I thought (probably more out of wishful thinking than anything) that it might, despite the reliable signal to the laptops, have to do with the distance from the router. That wasn't the case.

So when I looked at the settings in my router, I switched it to "Wireless-N only" and discovered what had by then been my hunch for a couple of days - that my receiver seemed to be caught in G-mode, because when I switched to N only, it was rendered unable to connect to the network, while the laptops (and my wired Windows XP machine) were working like a charm.

Being the Linux noob that I am, and having just barely gotten the thing to work with extensive help from online forum posts by people in my position, I'm at my wit's end on this one. It strikes me as some sort of driver issue. Any thoughts, guys? I'd really appreciate it.

rhe_green_bastard

---

