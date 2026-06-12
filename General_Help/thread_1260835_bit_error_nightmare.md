---
title: "bit error nightmare"
date: 2009-09-08
forum: General Help
---

### Post by PaulWhipp on 2009-09-08
I'm getting a nasty problem when I back up databases locally using mysqldump:

Running mysqldump on my system creates files that sometimes have 1 bit errors in them:
Notice the dash in these lines for example:
```

(51733,'2009-04-19',322,'activity',1,2335,'D80','am Walk','Saffy Pilbeam','D','D','M','TRI','Beagle',NULL,4),
(51734,'2009-04-09',322,'activity',6,2336,'D80','am Medication','Saffy Pilbeam','D','D','M','TRI'-'Beagle',NULL,4),
(51735,'2009-04-10',322,'activity',6,2337,'D80','am Medication','Saffy Pilbeam','D','D','M','TRI','Beagle',NULL,4),

```
And on another run dumping exactly the same database:
```

(51188,'2009-04-18',454,'activity',4,3045,'D56','pm Playtime','George Kobez','N','D','L','brown white','Boxer',NULL,3),
(51189,'2009-04-18',1561,'activity'-4,3039,'DS35','am Playtime','gemma bambry','F','D','L','blk/tan','Rottweiler',NULL,5),
(51190,'2009-04-19',1561,'activity',4,3040,'DS35','am Playtime','gemma bambry','F','D','L','blk/tan','Rottweiler',NULL,5),

```
And for a third time on exactly the same database no error was encountered.

And for a fourth time we get another error, this time a NULL becomes an unrecognised NULM.

I've reinstalled and the problem is still there. It seems to only occur after the system has been running for some time.

I suspect hardware but it seems strange that it has only affected mysqldump and perhaps large package downloads (I get frequent checksum errors).

I ran memtest to completion (no errors) and have tried checking out my swap partition but it seems to get mounted even if I boot the live CD so I'm not sure how to check it thoroughly for bad blocks.

Does anyone know how to scan and update the swap partition for bad blocks?

Any other ideas on how to track down this bizarre problem would be much appreciated too.

---

### Post by P4man on 2009-09-08
when you boot a live cd, it will swap on automatically, but you can just swap off again using "sudo swapoff -a" (or open partition editor, right click swap, and swapoff).

TBH, I suspect this is more likely a software than a hardware problem, but you never know...

---

### Post by PaulWhipp on 2009-09-08
Thanks P4man - I tried that but then it told me the partition was not ext2/ext3 so I thought I was off track.

I agree that it sounds more like software but its been plaguing mysqldump and synaptic package and repository updates very selectively though intermittently across 8.10 and two 9.04 installs.

I'm at a loss where to look in software for a common denominator.

---

