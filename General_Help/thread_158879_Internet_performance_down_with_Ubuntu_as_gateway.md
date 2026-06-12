---
title: "Internet performance down with Ubuntu as gateway"
date: 2006-04-11
forum: General Help
---

### Post by OfficeLinebacker on 2006-04-11
SO I've noticed that with Ubuntu replacing WIndows XP (with ICS) as the gateway/router for my network, pages seem to take muuuuch longer to load than before.

I am using dhcp-server which I believe uses DNS forwarding.

---

### Post by cleverselfreferentialname on 2006-04-11
Could you please give the specs for the system?

---

### Post by OfficeLinebacker on 2006-04-11
Sure.  Abit KR7A-raid with WDC 7200 RPM 250G HD and 2 GB memory.

Athlon Palomino running at 1.6GHz

2 10/100 NIC cards.

XP Box is 1.4GHz P4 with 1Gb RAMBUS Memory and unknown HD.

---

### Post by dcstar on 2006-04-11
[QUOTE=OfficeLinebacker]Sure.  Abit KR7A-raid with WDC 7200 RPM 250G HD and 2 GB memory.

Athlon Palomino running at 1.6GHz

2 10/100 NIC cards.

XP Box is 1.4GHz P4 with 1Gb RAMBUS Memory and unknown HD.[/QUOTE]
Have a look at the "disable IPv6" threads and see if they help.

---

### Post by OfficeLinebacker on 2006-04-12
I did this:

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

depmod -a

and it BROK Emy internet connection entirely.  I restored the old file.

Time to do some more digging.

---

