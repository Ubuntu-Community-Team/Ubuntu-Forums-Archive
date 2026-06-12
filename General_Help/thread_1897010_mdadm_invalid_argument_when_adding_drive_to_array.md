---
title: "mdadm invalid argument when adding drive to array"
date: 2011-12-18
forum: General Help
---

### Post by Kerbeh on 2011-12-18
I have a RAID0 array on ubuntu 10.04
Whenever I try and add an extra drive to it with:

```
mdadm --add /dev/md0 /dev/sdc1
```
I get add new device failed for /dev/sdc1 as 2: Invalid argument

I cant find any cause for this, However in the ubuntu disk utility sdc shows up as being used as a raid component. mdadm -D shows no mention of it but I cant figure out anything else it could be.

Is there a way to change the usage flag in the ubuntu disk utility or any other reason I cant add this drive?

---

