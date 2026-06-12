---
title: "Attempting to recover data from failed hard drive"
date: 2010-08-11
forum: General Help
---

### Post by Rob_Riv on 2010-08-11
I had some help in the IRC, but to positive outcome. I just want one last attempt at seeing if there's a solution. My Dell Studio 15 laptop HDD that runs Vista failed, I booted Ubuntu from a CD knowing that I should be able to recover my data.

However, Ubuntu can't find my HDD, it's not listed and "fdisk -l" doesn't result in anything. The BIOS seems to know that the HDD is there though.

Any ideas?

---

### Post by desnaike on 2010-08-11
If the drive has stopped spinning will be difficult indeed, but with one of my failed drives placing it in a external enclosure I was able to recover my data even though the drive barely spun.

---

### Post by Rob_Riv on 2010-08-11
> **desnaike said:**
> If the drive has stopped spinning will be difficult indeed, but with one of my failed drives placing it in a external enclosure I was able to recover my data even though the drive barely spun.
Sorry, I don't quite understand the advice.

---

### Post by desnaike on 2010-08-12
Sorry, if the drive mechanism has begun to die it's not spinning at 7200/5400/4200 rpm or whatever its rated at so you can't read the data but I have external hdd enclosures that I bought 1 for laptop drives 1 for desktop drives I place the drives in the enclosure and i'm able to read the drives and pull the data off. I currently have 9 old drives pulled from my servers after failling, recovered data from all but one the drive was completely dead.

---

### Post by Mark Phelps on 2010-08-12
I know it's a minor thing, but did you do "sudo fdisk -l", or just "fdisk -l".  The first will work, the second will not.  And, that's a lowercase L, not a one.

---

