---
title: "cdrom stops working"
date: 2009-07-25
forum: General Help
---

### Post by ricemark20 on 2009-07-25
My dvd rom stops working intermittently.  Sometimes in the middle of listening to a cd, or watching a movie.  Either dvdrom get same results.
Also, this worked fine in 7.10

OS: Xubuntu 9.04
AMD Athlon(tm) 64 X2 Dual Core Processor - 2.1GHz
2 Gb ddr2 ram
1 Gb Nvidia GeForce 8600GT
dvdrom 1: Sony DVD RW DW-D22A
dvdrom 2: Asus DRW-2014S1

Edit: added 'noapic' to kernel string in menu.lst

```
title		Ubuntu, Linux 2.6.31-11-generic 
uuid 		cb059232-b712-441d-91ce-5cfb54ee0d22
kernel		/boot/vmlinuz-2.6.31-11-generic root=UUID=cb059232-b712-441d-91ce-5cfb54ee0d22 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.31-11-generic

```

---

