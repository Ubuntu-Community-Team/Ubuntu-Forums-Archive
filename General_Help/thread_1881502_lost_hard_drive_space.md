---
title: "lost hard drive space"
date: 2011-11-15
forum: General Help
---

### Post by Total Noob on 2011-11-15
6 GB of space on the Windows XP partition of my dual boot laptop is unaccounted for. 

Properties indicates there are 18 GB total on the partition but the top level folders apparently only occupy about 12 GB, leaving the rest in limbo. Perhaps it is junk that Windows can't find or maybe a Trojan Horse?

I tried purging the space with Windows and purging the updates, and with freeware like ccleaner, but that was of limited success. Defrag also was of very little aid.

I tried Bleach Bit from the Ubuntu side over to the Windows side, and got a little help but not much.

Do I have any options using other repository Ubuntu apps to get the space back? I need it for work related proprietary software that is not available for Linux. I suppose if I knew how I could roam around in root and figure it out, but I'm not anywhere near that sophisticated. Installing apps to flash drives is OK but not really satisfactory and defeats the purpose of having a laptop because now you have to walk around with a lot of stuff.

In the past, I have been able to retrieve and affect the Windows partition from the Linux side to my advantage.

Thanks.

---

### Post by TeoBigusGeekus on 2011-11-15
Run 
```
df -h
```
from a terminal to see your partitions' sizes.

---

