---
title: "Wrong disk space reported in nautilus"
date: 2006-06-18
forum: General Help
---

### Post by NMUrugbysteve on 2006-06-18
Hey all, I just wiped my windows partition and absorbed that space into my home dir. All seemed to go well, but It's claiming that I only have 4 gigs free in nautilus, when in reality I have closer to 17 gigs free. Using the command 'du' shows the proper space though.

---

### Post by Omnios on 2006-06-18
I have similar problems with fdisk -l and and admin disks with fdisk showing my fat partition as ntfs and the admin showing fre space that is not there. In qtparted and when I was trying to install fedora core 5 it all showed as what it actualy was. I think this is a dapper bug.

---

### Post by mixx000 on 2007-12-10
Hey all,

have the same problem. In Nautilus it shows to me that the home-directory is ~400mb, but when I do a "du -h --max-depth=1 /" it shows me that the home directory has 5,9gb used space.

---

