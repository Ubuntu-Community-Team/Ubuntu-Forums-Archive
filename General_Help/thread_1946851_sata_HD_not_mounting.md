---
title: "sata HD not mounting"
date: 2012-03-25
forum: General Help
---

### Post by brandor64 on 2012-03-25
i have 3 HD's... 2 ide (80gb with ubuntu 10.04 installed, 100gb with win xp installed) and 1 sata drive with large folders such as music and videos.  
when ubuntu starts, the 100gb HD is listed in "places." this has never failed... but the 250gb SATA drive seems to be there only sometimes.  seems like no ryhme or reason, as i can restart the machine and there it will be, or maybe i have to restart 2x... 
when the drive is not listed, i can click through "system," "administration," "disk utility," and there it appears.  i can see it listed...  however, when i click "mount volume." i get the following message:
          Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed


i'd like the volume to be accessible upon start up.   
also i am running ubuntu 10.04

thanx

---

### Post by drdos2006 on 2012-03-25
From a terminal, run :  ls -l /dev/disk/by-uuid
Double click on /etc/fstab and check that the UUIDs match with your 250g HDD. 

Here is part of my /etc/fstab  file.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9fc76624-2a2e-4582-900b-3c0ea459dc4d /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=20cfc898-e723-46d1-9799-fff4d283786e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## /dev/sda2
UUID=9329e625-4dd5-45e9-94ba-e84d7685fafc  	/media/sda2	ext3	defaults	0	1
## /dev/sdb1
UUID=74ab1607-3998-4265-81b3-6cc936af422d 	/media/sdb1	ext3	defaults	0	1
## /dev/sdc1
UUID=36825a99-5389-4936-bc54-8586ea5b8c40 	/media/sdc1	ext3	defaults	0	1

Make sure that the mount point exists for your 250g HDD, if not then make a mount point with : sudo mkdir /media/sdc1 for your command.

regards

---

