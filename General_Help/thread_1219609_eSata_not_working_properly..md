---
title: "eSata not working properly."
date: 2009-07-21
forum: General Help
---

### Post by spydeyrch on 2009-07-21
Hey guys, fairly new to the forum here and somewhat new to Linux / Ubuntu. I have dabbled around with it in the past now and then just for fun but have been starting to use it more and more as an alternative to my Windows OS. Once I got out of the gaming niche in windows, I found that it wasn't as attractive as it used to be, so I have been making the switch over to linux. I still use windows as my main OS though just because it is "easier" for my wife and kids. Right now I have a triple boot: Vista x64, Ubuntu 9.04 x64, and OS X (hac) 10.5.6. Anyway, onto the good stuff. 

So my question/issue is this: I have 4 HDD that I am using: 1TB internal SATA (2 partitions - 750GB - Vista, 250GB - Ubuntu), 500GB internal SATA - OSX, 250GB external USB - OSX, 500GB external eSATA/USB/Firewire - Backup drive. Also my ODD (optical disk drive) is via SATA too. When ever I boot up ubuntu without the eSata HDD connected, during the boot, right before the ubuntu screen and progress bar show up, I get the following messages:

ata 1 softrest failed (device not ready)
ata 2 softrest failed (device not ready)
ata 3 softrest failed (device not ready)

then the system boots and I can see everything, all the drives (2 SATA, one ODD, and the external USB), so really it hasn't caused me that big of a headache, yet. The real issue is when I connect the eSATA and then boot. I get the three previous messages but also:

ata 10.00 failed to set xfermode (err_mask=0x4)

then the system boots. I can see all devices EXCEPT the eSATA drive. No other error messages, nothing. If I connect it via USB or Firewire, it works fine. I would REALLY like to get it working via eSATA for the obvious performance. Any ideas?

My hardware is as follows:

Asus M3A79-T Deluxe
AMD Phenom 9950 2.6 GHz oc'd to 3.2 GHz
790FX/750SB (Chipset)
4 Gigs DDR2 1066
ATI Radeon HD 3870
1TB internal SATA HDD (Seagate)
500GB internal SATA HDD (Seagate)
DVD Drive SATA
250GB External USB HDD (Western Digital)
500GB External eSATA/Firewire/USB HDD (Western Digital)

Any help would be MUCH appreciated!!! Thanks!! :D

-Spydey

---

### Post by spydeyrch on 2009-07-22
Anybody have any ideas or responses? :(

---

