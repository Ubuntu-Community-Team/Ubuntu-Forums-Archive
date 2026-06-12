---
title: "Raid 5+1 question"
date: 2011-04-29
forum: General Help
---

### Post by Haagimus on 2011-04-29
I currently have a Raid5 setup on FreeNAS 7.2 with 6x2TB disks for a total array of 12TB. My question is due to recent power outages and data loss, I am going to in the near future build another 12TB server and run Raid 5 on that as well and im thinking on implementing Ubuntu as the Raid controller. What I would like to know is after i copy all my data from the existing server to the new one, is can I create a Raid1 between the two seperate physical systems so I have basically got the most fault tolerance I can financially manage.
 
So question re-written:
Is it possible to have two stand alone servers running Raid5 configuration and link them through Ubuntu (10.10 flavor) to create a redundant Raid1 array between the two systems?

---

