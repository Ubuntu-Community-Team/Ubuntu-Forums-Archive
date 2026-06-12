---
title: "Server Edition DMRAID woes"
date: 2010-05-03
forum: General Help
---

### Post by maudigan on 2010-05-03
I'm having trouble getting my fakeraid setup working on 9.10 server edition.
 
I first tried the adaptec bios, and booted with the xubuntu 9.10 cd. DMRAID showed 4 mirrored drives instead of 4 RAID10 drives.
 
I swapped to the intel controler and rebooted xubuntu 9.10 and DMRAID showed the proper RAID10 setup. I activated "sudo dmraid -ay", and loaded gparted.
 
I selected the raid volume. I made a 12gig extension, and in that I made a 12gig linux swap(i have 12 gigs of ram). The remainder of the drive I set as ext4. I found nowhere in gparted to set the mount point to "/" which I understand to be important. 
 
I swaped CDs and booted with ubuntu 9.10 server edition. It detects the raid, and asks if I'd like to set it up, I say yes. The partition screen then shows 2 volumes measuring 250gigs. I'm assuming these are the two mirrors, and that they are showing 250 instead of 500 because the installers partitioner doesnt realise they are each stripped 500gig drives. (4 250gig RAID10) I go ahead and do "finish..." on the partition screen and it says I have no root setup. 
 
If I mess around with the partitions and let the installer handle it, it wont work cause the installer doesnt use dmraid from what I understand.
 
I rebooted xubuntu.
I used gparted to get the UUID of the raid volume. Edited fstab i believe with something like
UUID=blahblahblah / ext4 default 0 0
 
I retried my install steps and I get the same problem.
 
 
I'm utterly lost at what to try next. I want to point out that I have only setup a linux server once, with a checklist, so my knowledge is fairly limited. If someone offers help, I may have to get some clarification on some things =P Everything I outlined on here was from others posts/guides on the forums and google.
 
Any help anyone has would be GREATLY appreciated.
 
 
TL;DR - I'm using fakeraid with 9.10 server edition, I booted with livecd to build partitions with gparted and dmraid. Now I can't figure out how to set root on the ext4 partition during installation.

---

