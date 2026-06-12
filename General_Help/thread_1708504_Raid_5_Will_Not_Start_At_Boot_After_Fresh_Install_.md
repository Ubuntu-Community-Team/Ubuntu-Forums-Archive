---
title: "Raid 5 Will Not Start At Boot After Fresh Install Of Ubuntu 10.04 Alterntate"
date: 2011-03-16
forum: General Help
---

### Post by wgilthorpe on 2011-03-16
Sorry, but to adequately describe my problem I will have to be verbose.  I only ask for help after two solid days of research.  I have found much documentation on software RAID, but no one seemed to address my particular problem.I am running Ubuntu 10.04 LTS on a home media server.  I put the /boot /swap and / partitions on one disk and then created a three disk raid 5 array on which to store my media.  I edited fstab to auto mount the array on boot and all worked well for about 6 months.  My root drive (sda) failed.  I replaced the drive and reinstalled with the Ubuntu x64 alternate CD.  During the reinstall, I formated and partitioned the new root drive, but did not touch the 3 in the RAID array.  On boot, the raid array shows under computer and in the disk utility, however in the disk utility it shows as not running, partially assembled.  If I stop the array and restart (in the disk utility GUI), the raid array will start and all of my data is there.  I have gone through my /etc/mdadm/mdadm.conf file and all looks as it should, I believe, and I have run dpkg-reconfigure mdadm to no avail.  Any help would be awesome.

---

