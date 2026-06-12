---
title: "Wireless USB dongles compatible with Ubuntu?"
date: 2010-10-18
forum: General Help
---

### Post by t0p on 2010-10-18
I want to get a USB wireless dongle/card for my desktop computer (running 10.04).  But before I part with my hard-earned pieces of eight, I want to be sure that it will work with Ubuntu.  So here I am, to pick your brains.

There is a [Maplin]("http://www.maplin.co.uk") store near where I live, so I prefer going there rather than buying mail order.  I looked at the Maplin website this morning, did a [search for "USB wifi dongles"]("http://www.maplin.co.uk/Search.aspx?criteria=wireless+dongle") and I saw these: the [Belkin 150]("http://www.maplin.co.uk/Module.aspx?ModuleNo=396225") (£19.99); the [WB 300N]("http://www.maplin.co.uk/Module.aspx?ModuleNo=285314") (£19.99);  a [no-name "300Mbps N Wi-Fi USB Dongle]("http://www.maplin.co.uk/Module.aspx?ModuleNo=221130") (£24.99;  the [Belkin Surf USB Dongle]("http://www.maplin.co.uk/Module.aspx?ModuleNo=396211") (£24.99);  the [WB 54g USB Wi-Fi Dongle]("http://www.maplin.co.uk/Module.aspx?ModuleNo=218146") (only £14.99??); the [Netgear N150 Wireless USB Adapter]("http://www.maplin.co.uk/Module.aspx?ModuleNo=391315") (£19.99)... I could go one, but I'm sure you see that there are a lot of USB wireless adapters out there well suited for cheapskates like me.

So, I'd really appreciate it if you could give the Maplin search results a quick scan and advise me as to which adapters will work with Ubuntu, and those that won't.  Thanks!  Oh, and don't forget I'm a cheapskate.  The cheaper, the better... so long as the thing works!

---

### Post by Topsiho on 2010-10-18
Hello,

I see you still use Hardy Heron.
Since HH the wifi situation in Ubuntu has very much improved.
I have to wifi sticks, the first one did not work at all in HH, and is a 54MBPS 11G wireless adapter, as I remember, needing a madwifi driver. In later Ubuntu's (don't remember from which version, think KK) it worked flawlessly.
Sorry I don't remember which chipset it has.

The other one is very much newer, 150 MBPS 150N version with an AR9271 chipset from Atheros, needing a ath9k_htc driver. This one doesn't work at all in (a fully updated) Lucid Lynx, but I am very happy to report it does work very well in the Maverick Meerkat!

I think, but am not sure, that you are pretty safe with a 11G version of wifi, but have to be very carefull with the newer N versions.

That is: if you use a newer Ubuntu. I think in HH it is quite hopeless, this (from my experiences) being the wifi dark Middle Ages :)  (or rather :(  )

Succes,

Topsiho

---

### Post by coldraven on 2010-10-18
I suppose it depends what chips are in these dongles.
IIRC anything with an Atheros chip needed madwi-fi to work in HH.
I still need the proprietary driver with Broadcom chips in 10.04.
Not much help am I?

---

### Post by t0p on 2010-10-18
> **Topsiho said:**
> 
I see you still use Hardy Heron.


Thanks for the speedy response, Topshiho.

I don't use Hardy any more.  I installed Lucid just now, so I am now up to date (in LTS terms).  The dark ages are over!

---

