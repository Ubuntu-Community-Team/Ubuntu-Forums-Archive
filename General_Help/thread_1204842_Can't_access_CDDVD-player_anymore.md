---
title: "Can't access CD/DVD-player anymore"
date: 2009-07-05
forum: General Help
---

### Post by Vistaus on 2009-07-05
Since about 2 weeks, I can't access my CD/DVD-player anymore. Nero Linux and K3B give me an error. Nero Linux gives this error:

**One of the devices isn't accesible.** Check if your rights for the device are correct. Nero Linux has no acces to the following device:

 /dev/sg0 (SCSI Generic-device)

I already tried *sudo chown heimen-at-kubuntu /dev/sg0*, but nothing has changed.

I also tried booting from the Live CD (9.04). The CD/DVD-player works fine with the Live CD.
Also, the lens of the player is clean.

I'm using 9.04.
It's a laptop.

What to do about it?

---

### Post by Nevart on 2009-07-05
Were you using 9.04 two weeks ago when the drive was working?  Or did you recently upgrade?

This could possibly help...  

[http://ubuntuforums.org/showthread.php?t=1135452](http://ubuntuforums.org/showthread.php?t=1135452)

---

### Post by Vistaus on 2009-07-05
Yes, I was using 9.04 two weeks ago. In fact, I'm using 9.04 for about 2 months now.

Thanks for the reply, I read the whole thread you mentioned but nothing has worked. I tried the mount command, and the fstab thing, but the problem didn't go away.

---

### Post by Vistaus on 2009-07-08
Anyone? :(

This is what lshw says about my player:

id:
  cdrom
  description:   DVD-RAM writer
  product:   CD/DVDW TS-L632M
  vendor:   TSSTcorp
  physical id: 
  0.0.0
  bus info: 
  scsi@4:0.0.0
  logical name: 
  /dev/cdrom
  logical name: 
  /dev/cdrw
  logical name: 
  /dev/dvd
  logical name: 
  /dev/dvdrw
  logical name: 
  /dev/scd0
  logical name: 
  /dev/sr0
  version:   0A17
  capabilities:   removable audio cd-r cd-rw dvd dvd-r dvd-ram
  configuration:
   ansiversion  =  5
   status  =  nodisc

---

