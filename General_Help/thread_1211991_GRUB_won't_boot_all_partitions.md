---
title: "GRUB won't boot all partitions"
date: 2009-07-13
forum: General Help
---

### Post by shortridge11 on 2009-07-13
I'm quad-booting.  I have fedora 10, winXP, ubuntu, and Backtrack 4.  All was good until i updated my backtrack 3 to backtrack 4, and the partition with BT4 became partition that GRUB used to load.  Now i can't get ubuntu to load up, no matter how i tweak GRUB.  Honestly, I just want to use ubuntu's GRUB config, because that's the OS i use most.  I tried booting up an OS, and typing in the following:
```

grub

grub> root (hd0,6)

grub> setup (hd0,6)

grub> quit

xxxxx$ sudo reboot

```

through using gparted, I've determined that 6 is the partition that houses ubuntu, although i could be wrong.  i know numbering starts at 0, so rule that out.  I'm pretty sure ubuntu is on a logical partition though, so that may throw it off somehow.  If anyone knows a surefire way to find what number a partition is (based on the grub numbering system) please let me know

---

### Post by nacho32 on 2009-07-13
have you tried the [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) a must have tool

---

### Post by shortridge11 on 2009-07-14
yea...everytime i use SGD, after 5 minutes of selecting any option my computer is still stuck on the same screen. writing to the mbr doesn't take that long.  I can't get this computer to load grub from the right partition. any suggestions?

---

