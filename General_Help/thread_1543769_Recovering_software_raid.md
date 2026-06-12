---
title: "Recovering software raid"
date: 2010-08-01
forum: General Help
---

### Post by hebetude on 2010-08-01
I recently moved and had to take my server down.  When I hooked it back up at the new location, my software raid was not mounting.  Ubuntu would wait with a message "Wait for raid, or skip loading raid".

cat /proc/mdstat lists all my drives set as spare.  

Did I lose all of my data?

---

### Post by jacekk015 on 2010-08-02
Show us:

```
sudo mdadm --detail /dev/mdX - RAID dev
sudo mdadm -E /dev/sdX - disk drive that was on this RAID
```What kind of RAID?? 1, 5, 6, 10 ... ??

---

