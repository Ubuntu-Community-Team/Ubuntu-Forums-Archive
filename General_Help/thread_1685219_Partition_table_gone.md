---
title: "Partition table gone"
date: 2011-02-10
forum: General Help
---

### Post by OleR on 2011-02-10
I found a bunch of resources and threads with similar issues, but they did not resolve my problem - so please read on.

This morning my Laptop was working just fine. An hour later, after a clean shutdown, it would not boot anymore telling there was no bootdrive. I started up Ubuntu 10.10 Live CD, the harddrive was not mounted automatically. So I checked the Disk Utility, which found my harddrive, but claims its not partitioned. It is a ADATA S599 SSD Drive and should have 3 partitions on it: One for Ubuntu 10.10, one for Windows 7 and one for Data (maybe there is a fourth for swap, I don't remember). I checked the S.M.A.R.T. Data and did another SMART test, telling me there are 3456 Unallocated Sectors. Googling for that, I found out there was recently a firmware update for my drive supposedly fixing some of these issues. I did not install that update, and also not anything else the last time my system was running. So I hooked the drive in an external case via USB to a windows machine, because there is only a windows firmware update software from ADATA. The tool however did not recognize the drive. So I am guessing I will have to fix something before I can flash the firmware. I then found this help site: 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I ran testdisk and then parted and gparted - none of these found any partitions, even after Deep Search (in testdisk). So next step would be to image the whole drive on another external that I have flying around, but I guess if all these tools don't find anything, there is something seriously wrong. 

Any other ideas what I could try? Right now the only thing I can think of is imaging the drive and sending it off to ADATA on warranty. Then there are these tools for restoring single files, but that seems like the last resort. I still kind of hoping for some other way and don't really know how a drive can crash from working perfectly to being totally gone in like an hour - without anything unusual happening. Especially since the harddrive is only maybe 4 months old.

If you need any additional information, let me know, I just don't want to clutter the thread with stuff you don't need.

---

