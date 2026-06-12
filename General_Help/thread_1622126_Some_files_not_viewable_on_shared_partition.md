---
title: "Some files not viewable on shared partition"
date: 2010-11-15
forum: General Help
---

### Post by willibuster on 2010-11-15
*Short version:* I have a shared Windows/Ubuntu partition, but I can only see some of the files.  The amount of used/free space listed for the drive reflects the presence of the unviewable files.

*Details:* I am running dual boot Ubuntu 10.10/Windows 7.  Each OS has its own partition, plus I have an additional NTFS partition which I use for storing data that I'd like to be able to access easily from either Ubuntu or Windows.  From Ubuntu, I copied a number of files to the partition and had no problems through several Ubuntu reboots.  When I recently booted Windows, it listed the partition as completely empty.

I have now rebooted multiple times in Ubuntu and Windows, and I have created files on the partition from both Ubuntu and Windows.  Both OS's can see the new files, but not the old ones.  When I look at the properties of the partition, it tells me:

     Contents: 9 items, totalling 48.2 kb

but later states (pie chart)

     34.9 GB used

reflecting the files I expect to be there.  Remounting the volume has no effect, and du only counts the files I can see.

I'm really not sure what's going on here (and it may be the fault of Windows), but any ideas for how I might resurrect the missing files or more importantly prevent this from happening again would be great.  My important data is fortunately backed up, but I'd like to have a solution I can trust.

---

