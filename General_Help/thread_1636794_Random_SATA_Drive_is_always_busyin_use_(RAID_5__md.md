---
title: "Random SATA Drive is always busy/in use (RAID 5 / mdadm)"
date: 2010-12-03
forum: General Help
---

### Post by Dakhara on 2010-12-03
I have 4 SATA's in a RAID 5 array using mdadm. Yesterday when I started the computer the RAID did not build/mount.

When trying to load the array manually I get the message
"mdadm: cannot open device /dev/sd(a,b,c,d)1: Device or resource busy"
The drives should not be mounted or in use.

The output of the drives in mdadm (mdadm --examine /dev/sd_1) looks normal.

The weirdest part is that rebooting often changes which drive is marked as busy, it can be any of the 4 SATA drives.

Any suggestions on how to figure out why/what is being used and how to disable it?
I have tried searching for similar threads here and in google and haven't found anything similar or that worked.

Let me know if I should post any outputs as well.

Thanks!

---

### Post by SaturnusDJ on 2010-12-11
I would boot to Live CD, try to mount the array and see what's actually wrong.

---

### Post by dcstar on 2010-12-11
> **SaturnusDJ said:**
> I would boot to Live CD, try to mount the array and see what's actually wrong.

And look at threads like this:

[http://www.linuxforums.org/forum/ubuntu-linux/172560-random-sata-drive-always-busy-use-raid-5-mdadm-2.html](http://www.linuxforums.org/forum/ubuntu-linux/172560-random-sata-drive-always-busy-use-raid-5-mdadm-2.html)

That error message has many posts already on-line.

---

### Post by Dakhara on 2010-12-27
For future reference the suggestions from the above posted link worked.

[http://www.linuxforums.org/forum/ubuntu-linux/172560-random-sata-drive-always-busy-use-raid-5-mdadm.html](http://www.linuxforums.org/forum/ubuntu-linux/172560-random-sata-drive-always-busy-use-raid-5-mdadm.html)

Thanks to all for the help.

---

