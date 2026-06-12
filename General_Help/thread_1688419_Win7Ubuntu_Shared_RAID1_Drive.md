---
title: "Win7/Ubuntu Shared RAID1 Drive"
date: 2011-02-15
forum: General Help
---

### Post by turova on 2011-02-15
Hello,

I've researched this quite a bit and am still unable to find a good solution.  I have a dual-boot system (Win7/Ubuntu 10.04 for now).  I recently purchased two drives to create a mirrored array for backing up files.  

Since all Windows requires is a couple of clicks to set up RAID1, Ubuntu can do it with a single mdadm command, and all I really need to do is to simply copy all my data to two drives at the same time, I figured this wouldn't be much of a challenge.  Seems like I was wrong.

I formatted the drives with a single NTFS partition and was able to create a mirrored drive in Windows.  When I booted to Linux, I saw the two separate drives with identical contents.  I added these to a RAID array using mdadm and tried to open the resulting RAID drive that showed up in "Computer".  It wouldn't open because it seemed to have started a full mirror of the drives.  Once that finished, it still wouldn't open.  When I restarted, the RAID drive disappeared and Disk Utility shows the RAID array having 5 partitions, the last one having >18,000,000 TB.  Back in Windows, I can still see the files I copied onto it.

So my question is:  What is the best way to have a data backup using 2 drives that can be accessed from both Windows and Linux?  I don't want to create any hardware dependencies here (no fakeraid, RAID cards, etc.) to avoid problems if/when that hardware fails.  Any help is greatly appreciated!

---

### Post by ronparent on 2011-02-17
Mdadm sets up a linux software raid that is not compatible with s windows raid array based on a MB chipset. To use a raid in Ubuntu that can be used interchangebly with windows you need to uninstall mdadm and install dmraid. The two (mdadm and dmraid) are not interchageble.

---

