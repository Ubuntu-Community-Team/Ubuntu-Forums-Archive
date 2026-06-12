---
title: "No Mount Anymore!!! (Disk Changed to Fat16.)"
date: 2010-05-25
forum: General Help
---

### Post by DH Net on 2010-05-25
Major problem
I used Ubuntu 9.04 with 2 internal hdd drives one for the os and another for media storage (1 TB). So now when 10.04 was released the os must change. Before i install 10.04 LTS i install after format windows 7 because i need some applications. The first problem becomes when at windows 7 the second hdd (1TB) not shown at all. (The hdd is formated ntfs and running successfully on 9.04..) So i think that something do ubuntu and i didn't care because i will install 10.04.<So yesturday i install 10.04 Lts on my system and everything is quite good Exept the storage!!! 
I tried to many programs such a ntfs editor,mount edtr, and few more installed from ubuntu software center. Nothing at all.. so when i open the application "disk utility" i read that the hdd (1 tb) is partitioned as FAT 16!!! 
How done this and how i can recover all my data from there?
It's too important and i don't want to format it as the easiest solution..

Can someone help me ???
Thanks

---

### Post by bcbc on 2010-05-25
I've seen a few cases where an ntfs partition is shown as fat16. If you run ```
sudo blkid
``` it says ntfs but if you run ```
sudo fdisk -l
``` it says FAT16.

In one case the user changed it back to ntfs, but didn't specify how. Perhaps using sfdisk or testdisk.

I don't know if this will solve your problem.

---

