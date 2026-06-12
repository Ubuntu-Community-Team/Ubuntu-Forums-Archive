---
title: "PXE- E61 Media test failure, check cable WHAT THE..."
date: 2011-01-30
forum: General Help
---

### Post by shatanas on 2011-01-30
This has been going on for a while now, it was also occurring when I had Windows XP on my laptop. Sometimes when I turn on my laptop, the following comes up after post and the OS never loads:

Intel UNDI, PXE-20 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL 8139(X)/8130/810X PCI Fast Ethernet Controller v2.13 (020326)

PXE- E69: Media test failure, check cable
PXE-M0F: Exiting ROM

the last 2 lines just keep repeating.
Can anyone tell me how to fix this please. I would really like to just be able to turn on my computer without chance.

---

### Post by shatanas on 2011-02-01
bump

---

### Post by lavinog on 2011-02-01
PXE boot is when you boot using a network provided image.
It is usually configured in the system bios (under boot order)
Setting the hard drive as the first boot device should keep it from starting in this mode.

---

### Post by shatanas on 2011-02-02
ja....it always does. Except for those times that HDI:0 does not load i.e. boot menu only allows selection of RTL

---

### Post by lavinog on 2011-02-03
Is HDI:0 referring to the hard drive?
Is it possible that the drive could be failing?
How old is the drive?

---

### Post by shatanas on 2011-02-03
hmm, this has been mentioned before...maybe it is, given the age of over 4 years

---

