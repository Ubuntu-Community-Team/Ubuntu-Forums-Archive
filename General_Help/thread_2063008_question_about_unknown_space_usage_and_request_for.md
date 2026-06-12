---
title: "question about unknown space usage and request for solution"
date: 2012-09-26
forum: General Help
---

### Post by RFRFG on 2012-09-26
i'm running ubuntu 12.04 on a usb drive (installed from another live usb). i recently noticed that ubuntu is taking more space than it should(7.09gb) on my primary partition in gparted, but when i check in "computer" it shows only a bit less than 900mb both show 1.5gb remaining

for more information, i started with 9.10 )because my wirless card was having problems in 12.04 and 10.10 and i knew from past experience that it worked in 9.10) and upgraded to 12.04 from there. no external drives are mounted save the usb drive in which ubuntu is stored, and i unmounted my internal hdd.

---

### Post by RFRFG on 2012-09-26
bumb

---

### Post by steeldriver on 2012-09-26
I'm finding it hard to understand what you're asking exactly - what problem are you having here? Maybe open a terminal and post back the results of 

```
df -h
```

It may be that you are seeing the LiveUSB persistence file as 'usage'?

---

### Post by RFRFG on 2012-09-26
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       7.0G  5.3G  1.4G  80% /
udev            993M  4.0K  993M   1% /dev
tmpfs           402M  916K  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1003M  348K 1003M   1% /run/shm

```

1 would a normal install have the casper-rw file. i installed it using another usb, as i would to a hard drive. either way... wouldn't the persistence file translate to free space in ubuntu it's self...

and my question is are there any ideas what's happening, and how can i fix it (if possible)

---

### Post by RFRFG on 2012-09-27
in short... i have an 8 gig flash drive, normally installed (not through create live usb, or pendrive linux, etc.). the unity "explorer" (not sure the official term for this) says i have apx 500 mb remaining, and 2.7gb used. gparted and the above command report about 7.09gb used and apx 800mb free.

my question, Where's the space going? how do i solve it?


about the persistence file:
does it install with a normal install to a flash drive (never had this before)
wouldn't the persistence file translate to free space in the "explorer" or lake less space on the partition?
if this is the problem, can i just delete the persistence file and make a "casper-rw" partition for the persistency and fix it? (i don't see this working unless it's a bug)

---

