---
title: "hardware setup (dual ide vs one sata)"
date: 2011-04-12
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-12
I have a SAMSUNG SP0411C
40GB SATA
I also have 2 WD200-75CAA0
20GB IDE
I believe all drives have a rpm of 7200

If I were to put my home partition and everything else on separate drives would I get more speed out of it than one sata drive?

---

### Post by seawolf167 on 2011-04-12
It would be faster, yea, but I'm not sure you would really notice it unless it was setup as a RAID1 across both drives.

The main difference I think would be swap, if you computer dives into swap and you are able to put that on another disk, you'll definitely notice a speedup.

---

### Post by pqwoerituytrueiwoq on 2011-04-12
dam i forgot about swap where should i put my swap next to system or home :confused:
i think it should go on system's HDD unless i put firefox's profile on a ram disk 
i don't tend to use swap much anyway i have enough ram (4 gb)
*waits for motherboard to come in*
:popcorn:

---

### Post by seawolf167 on 2011-04-12
As a general rule, you should put swap on the disk that doesn't contain /

I'd start with / on one drive and /home & swap on the other drive. You can always move swap &/or /home back and forth if you want to, but this would probably be the ideal setup for that particular computer (especially if you don't think you'll use swap)

I suppose you could always add /boot to a different disk too, but I think there is a point for a personal computer where it gets overly complicated for no real reason

---

