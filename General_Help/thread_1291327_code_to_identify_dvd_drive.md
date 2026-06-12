---
title: "code to identify dvd drive"
date: 2009-10-14
forum: General Help
---

### Post by gotanothergrot on 2009-10-14
I need to find out what type of DVD's my drive records on, is there a code which will tell me? Thanks

---

### Post by StuartN on 2009-10-14
> **gotanothergrot said:**
> I need to find out what type of DVD's my drive records on, is there a code which will tell me? Thanks

Yes, **sudo lshw -class disk** will present output like this:

```
  *-cdrom
       description: DVD writer
       product: DVD+-RW AD-5540A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 102C
       serial: [Optiarc DVD+-RW AD-5540A102C Jul04,2006
       **capabilities: removable audio cd-r cd-rw dvd dvd-r**
       configuration: ansiversion=5 status=nodisc
```

The bit in bold lists the media types.

---

### Post by gotanothergrot on 2009-10-14
Thanks for the help Stuart, :) Looks like i can burn to most formats :P
Excellent.

---

### Post by gotanothergrot on 2009-10-14
screenshot

---

