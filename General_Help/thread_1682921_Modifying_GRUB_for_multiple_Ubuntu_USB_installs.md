---
title: "Modifying GRUB for multiple Ubuntu USB installs"
date: 2011-02-06
forum: General Help
---

### Post by morningsunshine on 2011-02-06
Hi All,

I have 2 portable HDDs - both 500 Gb. I had been booting lucid from a USB HDD1. In my laptop, I have a 100Gb disk - dual boot Windows XP and hardy. 

Until now, the boot order allows me to boot into either of these easily.

Today I did these changes:

1. Replicated lucid on HDD1 to HDD2
2. Removed 100Gb disk and put HDD1 inside

Now the boot menu shows lucid, hardy n XP entries. Only lucid entry works, though.

When I try to plug HDD2 and boot from it, system still takes HDD1 for boot. BIOS is configured to check for USB boot before HDD. 

So essentially, I'd like to be able to:

a. boot into any of HDD1, HDD2, 100Gb disks; and 
b. boot menus for HDD1, HDD2 lucids, 100Gb XP + hardy should come only when their respective boot disks are plugged in.

Please let me know if this is feasible.

Many Thanks,
sunshine

---

