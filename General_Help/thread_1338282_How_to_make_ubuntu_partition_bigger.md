---
title: "How to make ubuntu partition bigger?"
date: 2009-11-26
forum: General Help
---

### Post by bryan4 on 2009-11-26
i have partition win xp and ubuntu 9.04 on my computer. but i wanna make the size of ubuntu bigger. i wanna get rid of xp? whats the easy way to do that?

---

### Post by MelDJ on 2009-11-26
do you want to resize the ubuntu partition or delete windows?

---

### Post by audiomick on 2009-11-26
Try reading this:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you want to get rid of windows completely, you can simply re format the partition to one that has a linux file system on it.

_**But**_ this will likely mess your grub. This is easy to fix, but I don't know exactly how.

Someone asked exactly this question last night, and got an answer. Maybe if you search a bit, you can find it. It was in General help or installations & upgrades.

---

### Post by dandnsmith on 2009-11-26
> **bryan4 said:**
> i have partition win xp and ubuntu 9.04 on my computer. but i wanna make the size of ubuntu bigger. i wanna get rid of xp? whats the easy way to do that?

Boot from a liveCD which has gparted.
Use that to delete the XP partition.
If that was the first, as previously said, the grub arrangements will be disrupted and you'll probably need to re-install grub.
You can use gparted from the liveCD to expand the Ubuntu partition, when you've deleted the XP partition.

There is a tool for sorting out the booting mess, which can be got on a liveCD - memory fails me as to the name, but I think you want the 'Super Grub Disk'.

---

