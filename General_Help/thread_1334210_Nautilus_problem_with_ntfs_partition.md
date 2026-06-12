---
title: "Nautilus problem with ntfs partition"
date: 2009-11-22
forum: General Help
---

### Post by pablopancho on 2009-11-22
Since I didn't find any thread about this problem I decided to create a new one.

I have an external usb drive (Western Digital) with two ntfs partitions WD1 and WD2. Very often I copy some video files from my home folder to one of the folders in the second partition. I normally do it this way: 
1- I copy several video files to the Video folder on WD2. 
2- I drag and drop single video files to a couple of subfolders of Video folder.

The problem: After I drop the video file on a subfolder icon and the file is moved there I enter that subfolder. Nautilus cannot list any files in this subfolder, just pointer is showing busy. I can browse everything else on the disk but not this folder.

I wanted the external disks to be mounted on system startup so I configured them with default settings in pysdm.

I think it is a Nautilus problem because I can freely browse that folder with krusader or bsc. I used bsc to rename one file in the affected folder and after that Nautilus shows that file but no others (cursor still busy). Ntfsfix doesn't find any problems. Unmounting and mounting doesn't help.

I'm using karmic 64bit on Dell XPS m1530 laptop.

I'd appreciate any help. Thanks.

Edit: Restarting system somehow helped this time but this problem occurs way too often to me...

---

