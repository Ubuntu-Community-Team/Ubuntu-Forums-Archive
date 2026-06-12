---
title: "Raid LVM Discussion and Troubleshooting"
date: 2010-02-26
forum: General Help
---

### Post by FeraTech on 2010-02-26
This really isn't a cry for help but more of an inquiry for insight. It took me several days to find a configuration that was even usable on a system that should be screaming fast.

I've tried several different raid configurations and here is my experience. 

Hardware:
Quad Core AMD
Gigabyte Board with 4gig DDR3 Ram
2 x 1500gig Sata2 WD Drives with 64mb cache each

_First Try_
Raid 1 Swap 50gig
Raid 1 Root 1450gig EXT4
This was so slow that it wasn't even usable. When the drives would resync it would take firefox 10 min to come up.

_Second Try_
Raid 1 Swap 10gig
Raid 1 Root 1490gig EXT4
A little faster but the smaller swap didn't help. It seems  like when both partitions decide to resync you are screwed.

_Third Try_
Raid 1 Swap 10gig
Raid 1 Root 1490gig EXT3
Don't know why I even bothered with EXT3 ohh man was this slow. Even the installation took almost twice as long.

_Fourth Try_
Different Approach
Raid 1 1500gig (both drives)
LVM on raided drives
LVM Swap 10gig
LVM Root 1490gig

This way the drives only resync once. This works amazingly well. It was the first time I ever tried LVM and I must say I'm very impressed and it also comes with a lot of advantages. 

I am just wondering if my current setup is normal and if there are any better ways to squeeze out performance.

Pretty much I am mainly looking to make sure my data is safe. I also do full weekly backups of the file system.

---

