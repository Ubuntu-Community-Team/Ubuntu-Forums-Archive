---
title: "RAID hangs system. Manual reboot required."
date: 2012-04-17
forum: General Help
---

### Post by kingrolo on 2012-04-17
I keep getting a lock-up on my RAID5 server. From time to time when the disks are being used 'something' locks up and any subsequent calls involving the RAID (eg. ls, mdadm) will hang. I can still ssh a new shell and perform other unrelated tasks, but the only way to fully recover is to switch off! As this is also my MythBackend it's a pain as it often occurs during a recording. I don't understand the logs and can't tell what is the root cause of the problem.:confused: Please can someone point me in the right direction.

For added confusion I've named my server 'Solaris' ;)

Ubuntu 11.10 64 bit..
Linux Solaris 3.0.0-17-server #30-Ubuntu SMP Thu Mar 8 22:15:30 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Supermicro AOC-SASLP-MV8 SATA adapter with 5x2TB drives in software RAID5.

kernel log is attached.
Please let me know if I need to provide more information.
Many thanks,
Peter.

---

### Post by kingrolo on 2012-04-19
Anyone? Is this the best place to post this question?:confused:

---

### Post by zdea on 2012-05-28
I'm experiencing this as well. Haven't found any solution or even a hint as to what is going on... as you mentioned... touching the array in any way (ls for the mount point, trying to access it via samba share, etc) hangs whatever process. No CPU usage is happening so nothing's infinite looping to my estimation.

---

### Post by kingrolo on 2012-05-29
Hello zdea,

The log files don't mean a lot to me, but as they do contain a lot of 'xfs' related errors I decided to try reverting from XFS back to trusty ext4. I haven't had the problem since i did this.

on a side note..what made me take such a leap was that on one of my frequent and obligatory power cycles to recover the blockage the array went to **** and I lost 5TB of data (not backed up). When you're a home user it's hard to weigh the cost of hard drives against the value of your data. Mine was several years of recorded TV off-air, so not irreplaceable, but gutting all the same.:mad:

---

