---
title: "Actual capacity of /home in SAMBA drive not showing"
date: 2010-07-08
forum: General Help
---

### Post by anuvnu387 on 2010-07-08
Hi,

I have a Lucid Lynx server running with a 6 GB for /home and a data partition of 400 GB mounted inside home (/home/user/data). The data partition is shared through SAMBA for access by other windows machines on the network. However, the capacity of the samba share shows up only as 6 GB (or less) while the actual capacity is 400 GB. I am assuming that this because it is mounted within the home partition. I understand that 400 GB is still available even though the SAMBA drive shows only 6 GB (or less) capacity. 

The problem is, I am trying to setup Windows 7 Backup and Restore on one of my laptop. The backup stops with an error that the network drive does not have enough disk space. I think that this is because the samba drive only shows up as 6 GB or less capacity even though it can store more. 

How do I fix this problem? How can see the actual size of the SAMBA drive (in my case 400 GB) in stead of the remaining space in /home partition?

I know I can reformat my drive and make my /home 400 GB. But I am not sure if this will fix the problem. However, I will prefer to this without formatting.

Thanks for the help.

---

### Post by anuvnu387 on 2010-07-09
Nevermind. I used GParted to rearrange/merge partitions. It look several hours to move 1.5 TB of data though. Anyway, now I made the home partition 400 GB with the "data" folder inside it. Now when the drive is mapped through Windows it shows the actual 400 GB. And no problems with my Windows 7 Backup and Restore. Just though this might help someone.

---

