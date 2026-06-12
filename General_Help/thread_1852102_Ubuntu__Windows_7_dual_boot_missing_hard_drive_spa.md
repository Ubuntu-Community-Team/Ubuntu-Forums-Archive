---
title: "Ubuntu / Windows 7 dual boot missing hard drive space"
date: 2011-09-29
forum: General Help
---

### Post by bajones234 on 2011-09-29
Hello, 

About 6 months ago I set up a new machine dual boot using Grub2 with the following configuration:

/dev/sda1 ntfs (windows 7 system reserved) 100 MB
/dev/sda2 ntfs (Windows 7 C: drive)  99 GB (includes 4 GB of preloaded page file space)
/dev/sda3 ntfs (Shared drive - Windows/Ubuntu) 801 GB
/dev/sda4 extended partition 32 GB
    /dev/sda5 ext4  (Linux Root) 30 GB
    /dev/sda6 linux-swap 2 GB

I set it up so that I could access sda3 from either the windows or ubuntu operating system.  It has worked perfectly so far.  But, here is the problem.

For some reason as sda3 grows Windows thinks that the windows system drive (sda2/c:drive) is also growing.  So that now I have a low storage warning stating that there is only 8.76 GB of free space left on my C: drive (sda2) when in reality there should be about 77 GB of free space.  I've made hidden files/folders viewable so I know what should be on the drive.  The difference is nearly exactly the size of my shared drive (sda3/E:drive).  

I removed the shortcut that I had from the C: to the E: drive on the windows side, as I read that could cause a problem.  There was no change however.  Could this still be a shortcut link problem? Has anyone else had this problem in a dual boot scenario?


----

O.k. well the culprit (found using CCleaner) was Windows/Temp files.  Still not sure why there were 67GB of temp files here (or why they didn't show up until I opened the folder).  But, anyway, CCleaner removed them and all is well for now.  Though I get the sense that windows is creating temp files of my shared drive for some reason (even with System Protection turned off for that partition).

---

