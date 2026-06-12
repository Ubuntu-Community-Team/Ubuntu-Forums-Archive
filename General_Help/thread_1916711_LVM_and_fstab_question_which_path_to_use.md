---
title: "LVM and fstab question: which path to use?"
date: 2012-01-28
forum: General Help
---

### Post by fitzhugh on 2012-01-28
Let's say I have a volume group super creatively named "vg001" with a logical volumes "lv001" and "lv002", and are mounted in /media/ 

There are two paths to the logical volumes that I can use in fstab:

```
/dev/mapper/vg001-lv001   /media/lv001 defaults      1  2
/dev/vg001/lv002          /media/lv002 defaults      1  2
```


Both work, and I see them created by different tools: system-config-lvm does it one way, pysdm does it the other. 
Is this entirely trivial? Any idea on which is 'correct'? Any problems with doing it one way or the other?

---

