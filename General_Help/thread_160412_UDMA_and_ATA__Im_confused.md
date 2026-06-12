---
title: "UDMA and ATA?  Im confused"
date: 2006-04-14
forum: General Help
---

### Post by underwater on 2006-04-14
Basically when i do a dmesg | grep -i udma

I see 

[4455232.869000] ata1: dev 0 configured for UDMA/100
[4455234.085000] ata2: dev 0 configured for UDMA/33


This is a laptop (Dell Inspiron 6000)

This confuses me does it mean one drive is 33 and one is 100, or is something not set correctly in the software for one drive?  How can I figure out which drive is 33 or 100?  (I have a dvd writer and a hard drive)?


I see a lot of threads about enabling dma, but I'm not even sure if I need to?  

Umm yeah what's my first step?  is anything even wrong?

---

### Post by dcstar on 2006-04-15
[QUOTE=underwater]Basically when i do a dmesg | grep -i udma

I see 

[4455232.869000] ata1: dev 0 configured for UDMA/100
[4455234.085000] ata2: dev 0 configured for UDMA/33


This is a laptop (Dell Inspiron 6000)

This confuses me does it mean one drive is 33 and one is 100, or is something not set correctly in the software for one drive?  How can I figure out which drive is 33 or 100?  (I have a dvd writer and a hard drive)?


I see a lot of threads about enabling dma, but I'm not even sure if I need to?  

Umm yeah what's my first step?  is anything even wrong?[/QUOTE]
```
sudo hdparm -i /dev/hda
sudo hdparm -i /dev/hdb
sudo hdparm -i /dev/hdc
sudo hdparm -i /dev/hdd
```
will tell you what all of your drives are operating in.

Modern hard drives are usually UDMA/100 (UDMA5), DVD/CD drives are usually UDMA/33 because the performance bottleneck is in the drive, and a faster connection is not of any use whatsoever.

There is probably nothing wrong with your system at all.

---

