---
title: "low disk space"
date: 2011-02-26
forum: General Help
---

### Post by DougLux on 2011-02-26
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d136c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9347    75078656   83  Linux
/dev/sda2            9348        9730     3069953    5  Extended
/dev/sda5            9348        9730     3069952   82  Linux swap / Solaris
doug@doug-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               76G    70G   2.7G  97% /
none                   519M   254k   519M   1% /dev
none                   525M   771k   524M   1% /dev/shm
none                   525M    95k   525M   1% /var/run
none                   525M      0   525M   0% /var/lock

having a problem: disk usage analyzer claims my disk is almost full, something is filling it up. Had a problem while printing off a web page via Opera, the printer keep printing the page endlessly. Since then I noticed a slow down and a couple of warnings have appeared claiming low disk space. Anyone help?

---

### Post by cjhabs on 2011-02-26
If it is due to printing, you can check the queues with "lpstat -o".
You can cancel jobs with the "cancel" command.
Check the "man" page for the cancel syntax.
Canceling the job should free up disk space from the root partition.

---

### Post by tgm4883 on 2011-02-26
> **DougLux said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d136c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9347    75078656   83  Linux
/dev/sda2            9348        9730     3069953    5  Extended
/dev/sda5            9348        9730     3069952   82  Linux swap / Solaris
doug@doug-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               76G    70G   2.7G  97% /
none                   519M   254k   519M   1% /dev
none                   525M   771k   524M   1% /dev/shm
none                   525M    95k   525M   1% /var/run
none                   525M      0   525M   0% /var/lock

having a problem: disk usage analyzer claims my disk is almost full, something is filling it up. Had a problem while printing off a web page via Opera, the printer keep printing the page endlessly. Since then I noticed a slow down and a couple of warnings have appeared claiming low disk space. Anyone help?

To be fair, your root partition is getting pretty full. I get warnings at work when mine reaches less than 10GB free.

Not sure that would cause those strange printing issues though.

---

### Post by DougLux on 2011-02-26
thanks for your reply to my plea for help, I tried the "lpstat -o , and opened the man lpstat, other than find printer location and serial number I have yet to clear the problem gobbling my drive, anymore suggestions would be appreciated.

---

### Post by DougLux on 2011-02-26
The problem is that the root directory is filling, this is a recent problem, I did have plenty of room in root until the problem began.                                                                                                                                                       I am assuming it has something to do with the print problems I had so I immediately shutdown the printer and removed Opera (thinking the conflict was due to Opera) I am also thinking  the log files in /var but have no way of pinpointing the error.

---

