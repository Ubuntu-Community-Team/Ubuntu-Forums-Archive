---
title: "Ubuntu with Windows"
date: 2005-01-31
forum: General Help
---

### Post by Grey on 2005-01-31
Hello everyone.  I've tried out a few distros in the past, but I have to say that I finally found one that I could stick with when I found Ubuntu.  It's been installed on my PC for a few months now, and I have no plans of removing it.  But the problem is that it's not really fully functional as it stands, and I have to boot Windows in order to get much of anything done.  There are 2 reasons for this.

1)  I can't figure out a good way of managing common storage between Windows and Linux.  I use NTFS partitions for bulk file storage, because Windows will only read FAT32 and NTFS to the best of my knowledge.  NTFS offers huge benefits over FAT32, and I am not really willing to keep around huge (about 120GB) FAT32 partitions.  I am able to read the NTFS partitions in Linux, but I am unable to write.  I am aware that there's a way to enable writing support... but I am a little concerned about that, as I have absolutely no idea how well it will work, and I have a lot of data to lose.  I was hoping that someone here could tell me just how safe writing to a NTFS partition is from Linux.

2)  I have 3 hard drives.  A 160GB drive that I keep vital data on, as well as 40GB set aside for Linux.  My other 2 are in a RAID-0 configuration, and run Windows, Games, and Applications.  The RAID-0 drives also house my new downloads, and stuff that overflows from my main hard drive now and then.  I would like to access this drive in order to store my new downloads if nothing else.  But I have my pick of a Promise Fasttrak 378 or a Promise Fasttrak TX2000 to run.  I have been completely unable to compile the kernel module for either of those RAID controllers, and I have about given up.  (possibly incompatable with 2.6 kernels).  If anyone can point me in the direction of a debian package for a Fasttrak 378, I would be most appreciative.

---

