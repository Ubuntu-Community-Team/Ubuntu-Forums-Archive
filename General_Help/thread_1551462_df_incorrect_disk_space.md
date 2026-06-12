---
title: "df incorrect disk space"
date: 2010-08-12
forum: General Help
---

### Post by GlazedWicker on 2010-08-12
I just finished my computer build and have installed Ubuntu lucid as my sole OS. Everything seems to be going well except for the fact that when I do "df -h", the size of my 1TB hard drive is reported as being only 908GB. I could understand if it was off by a few gigs but 92? The result is the same with the graphical "Disk Usage Analyzer." However, Under System>Administration>Disk Utility the correct number is displayed. There is probably a simple explanation for this but I can't for the life of me figure it out. Anyone?

---

### Post by dabl on 2010-08-12
Check the "Capacity Measurement" table down this page:

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)

---

### Post by GlazedWicker on 2010-08-12
I see. I still don't fully understand if I'm indeed unable to use almost 100GB of my drive or if Ubuntu is simply reporting the wrong size. I'm inclined to believe the latter..

---

### Post by dabl on 2010-08-12
You are able to use all of your hard drive.  The drive manufacturer advertised it as 1000Bytesx1000x1000x1000x1000=1T.  Linux (and DOS/Windows) will read it as (measured number of bytes)/(1024Bytesx1024x1024x1024x1024)=0.91TB, approximately.

---

### Post by 0004tom on 2010-08-12
Do you have a swap partition?

---

### Post by GlazedWicker on 2010-08-12
Ah that makes sense. And yes, I do have an 11 gig swap partition so that would account for some of the missing space. Thanks for the help.

---

