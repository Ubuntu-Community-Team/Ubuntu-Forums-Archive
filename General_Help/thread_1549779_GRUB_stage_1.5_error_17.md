---
title: "GRUB stage 1.5 error 17"
date: 2010-08-10
forum: General Help
---

### Post by crewmager on 2010-08-10
well, i was using dual boot in a hard disk, Ubuntu and Vista. The reason of my problem is deleting the disk volume of Ubuntu by using Vista's Disk Management tool and formatting ubuntu and then i changed the filesystem to NTFS.After restart, i had this GRUB stage 1.5 error 17 and then cannot touch anything. How can i direct booting Vista initially and avoid that problem. Any help will be greatly appreciated.

---

### Post by Mark Phelps on 2010-08-10
To directly boot Vista, you will have to replace the MBR with one from Vista and possibly repair the Vista boot loader as well.

Since you probably do NOT have a Vista Repair CD, go to the link below, download the appropriate Vista version and burn it to CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you have that CD, boot from it, select Startup Repair, and run that three times.  IT will take all three passes to make the repairs.

---

### Post by touchthestove on 2010-11-07
I have similar problem. I have a Toshiba laptop with 1 HDD. It is divided into 2 partitions, first one for Windows Vista, second for Ubuntu 10.04. One day when I shut my PC down incorrectly I started to get the grub loading screen and error 17. I cannot even choose OS just because I don't see GRUB menu list. I have a flash drive with Ubuntu 10.10. Is it possible to use it as Live CD? And what should I do to fix this problem?

---

