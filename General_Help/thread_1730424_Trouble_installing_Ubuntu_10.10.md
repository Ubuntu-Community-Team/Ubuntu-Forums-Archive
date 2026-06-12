---
title: "Trouble installing Ubuntu 10.10"
date: 2011-04-16
forum: General Help
---

### Post by geekcalledsick on 2011-04-16
Hello,
   
  I have Compaq Presario CQ62-215DX notebook (laptop) computer with built –in image of Windows 7. I use partitioning tool to create partition of 250GB harddrive. I created these partitions as NTFS partition.
   
  My issue is after creating partition of 75GB whereby I want to install Ubuntu using ubuntu-10.10-desktop-i386.iso file from dvd drive; I cant install.
   
  I use ext4 file system to install ubuntu and mountpoint is root \ 
   
  After user setup it stops at this point:
   
   UBUNTU CRON [9354]: (root) CMD (cd/run-pats—report/etc/cron.hourly)
   
  It doesn’t install ubuntu on separate partition. 
   
  Could someone please advise me how to install ubuntu on separate logical partition? Windows 7 is in primary partition.

---

### Post by zvacet on 2011-04-16
First check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of your iso.If is correct then burn it on lower possible speed and then when you boot check disc for errors.If everything is fine go for install.You said that all your partitions are NTFS so choose manual way to install and one of those partitions format as ext4 and mark it as root /.If your md5sum is not right download same iso with torrent and point download where exiting iso is.Torrent will just replace bad files with good ones,so you will not download all files again.After that run md5sum and proceed with burning disc and installation.

---

