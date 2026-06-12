---
title: "Rebuilding RAID1 issues"
date: 2009-11-07
forum: General Help
---

### Post by JohnUt on 2009-11-07
My upgrade to Karmic went well, I even got a message from the utility Palimpsest saying that one of my drives in my RAID1 had many bad sectors. I purchased a same sized drive from Newegg and replaced the one that was failing. I used Palimpsest to add the new drive to the RAID1 and it took quite awhile and it then said everything was fine.

sudo mdadm --misc -D /dev/md0 also said that both drives in the array were "active sync" so I felt pretty confidant that I had successfully rebuilt the RAID. When I looked at the drives with Gparted the first drive looked normal but the new supposedly successfully added to the array drive said its status was not mounted and didn't have the same partition setup. So what more do I need to do to make return this RAID to normal operation, or is it there now?

Tried to reboot with the new drive only and crashed big time, so it isn't working, now just not sure how to fix it from here.

Tried to rebuild with terminal commands after manually setting up drive with Gparted. It took about and hour and a half and had the same results.

---

