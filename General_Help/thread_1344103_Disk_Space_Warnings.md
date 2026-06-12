---
title: "Disk Space Warnings"
date: 2009-12-02
forum: General Help
---

### Post by StoicKoi on 2009-12-02
I am running Ubuntu 9.10 dual booting on a EEE 1005HA. Lately I have received warnings that my avalible disk spave is low (around 100MB) but why I open the Disk Usage Analyzer (linked in the warning) it says I have 67GB free. Anyone know why I am getting these warnings and how to make it so it warns me when I actually am low on space?

---

### Post by jbrown96 on 2009-12-02
I think that the EEE has two hard drives. Perhaps one of them is filling up. Let's check out your partitions ```
mount -l | grep /dev/sd.*
``` This should give you something similar to what I get > /dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sda5 on /home type ext4 (rw)

I have two separate partitions mounted. I could get errors if either fills up. Let's see how much space you have available. We need to location where the partitions are mounted. For my first one, /dev/sda1 is mounted on /, so I use /, and the second one, I use /home. ```
df -hsx /home /
``` is the command that I would run; you need to replace those locations with what you found previously.

Here's what I get > Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             134G  106G   22G  83% /home
/dev/sda1             6.5G  4.7G  1.5G  77% /

It's importnat to note that the last 5% of every parition is saved for the system, so you can't go beyond 95% full, unless you use tune2fs, but that's not recommended.

---

