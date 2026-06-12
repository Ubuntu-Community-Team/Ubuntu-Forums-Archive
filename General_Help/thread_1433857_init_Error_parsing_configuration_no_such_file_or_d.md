---
title: "init: Error parsing configuration: no such file or directory"
date: 2010-03-19
forum: General Help
---

### Post by ternarybit on 2010-03-19
Some background:
[LIST]
[*]Asus P5W DH Deluxe motherboard
[*]Intel Core2 Quad Q9550 @ stock 2.83GHz
[*]4GB OCZ Reaper HPC @ 416MHz (slight overclock to allow proper CPU frequency)
[*]Ubuntu Jaunty Jackalope (9.04) x86_64
[*]Kernel 2.6.28-11-generic, recently updated to 2.6.28-18-generic
[*]2x Western Digital 250GB HDD (WD2500AAKS) RAID1 mirror w/ mdadm as follows:
[*]sda1 + sdb1 = md0 mounted as / (root)
[*]sda5 + sdb5 = md1 mounted as /boot
[*]sda6 + sdb6 = md2 mounted as /opt
[*]sda7 + sdb7 = md3 mounted as /home
[/LIST]

Last night I ran updates which included the kernel listed above. I finished my work and shut down as normal. This morning I booted and got dumped into a basic command line. I rebooted into Trinity Rescue Kit to run fsck on all 4 md disks.

I ran fsck -fy /dev/mdX on all 4 md disks. md0 had several errors which were fixed automatically. I did not note these errors. All other md disks came up clean, but I force checked them anyway with no problems.

Rebooting brought me to the usual Ubuntu loading progress bar, which locked as the progress bar segment sat about 1/4 from the left. (e.g. [========|=========================]) The HDD light was inactive, and I let it sit for about 60 seconds before hard rebooting.

Next, I tried to load the recovery kernel. Loading both versions of the recovery kernel halted at this error:

```

Begin: Running /scripts/init-local ...
Done.
Begin: Running /scripts/init-bottom ...
Done.
init: Error parsing configuration: no such file or directory
[9.23426XX] Kernel panic - not syncing: attempted to kill init!
[9.23426XX] Dumping ftrace buffer:
[9.23426XX]     (ftrace buffer empty)
```

I rebooted into TRK and tried a manual fsck on all 4 disks again, all came up clean. I then ran 1 pass of Memtest v2.11 which came up with no errors. Searching for other threads with this error didn't turn up anything relevant to my situation.

The obvious question is how to fix this problem. The next question is how did this happen? I truly love Linux and Ubuntu specifically, but it's quite frustrating to feel like my OS just randomly breaks. Any ideas?

---

