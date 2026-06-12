---
title: "messed up win7 while installing ubuntu"
date: 2009-12-22
forum: General Help
---

### Post by wolfy1889 on 2009-12-22
Hello,
Im very new to linux. I have a acer aspire 5739g. I was going to dual boot win7 and ubuntu. I had win7 installed fine and booted up in live cd and started gparted and made a partition for ubuntu. Since it was my first time using ubuntu I was playing around with it and seeing what gparted could do and I formatted my windows 7 partition by clicking the create instead of cancel in the "create partition table" screen. 
So I completely reformated the drive and got rid of the partitions to install windows 7 again but then the cd wouldnt boot and just went to a screen that said "grub rescue>". But my ubuntu and backtrack cds booted fine. 
So right now I have the full drive formated too ext4 and have ubuntu on it. I figure it has something to do with my mbr not showing the windows boot loader so my cd wont load (if that makes sense, but what with windows does). So I was thinking maybe I just need to fix my mbr. Or is it cause my win7 cd is just an upgrade disc and my laptop didnt come with a vista cd. But when I got the upgrade cd I completely formated my drive to install win7 and didnt have an issue but right now Im trying to scrounge up a vista cd from a friend but its late and I might not see him for awhile. Iam trying to download a windows 7 recovery cd though.
Any suggestions?
Sincerely,
Steve

---

### Post by wilee-nilee on 2009-12-22
You can shrink the ext 4 Ubuntu and leave a open space for the W7 install choose the custom install and point it at the open area to format and install. You can also setup the computer with a ntfs partition with gparted that W7 will go into to. The only thing that will happen is that you will have to use a live Cd of the Ubuntu to get grub back there are lots of threads on this.

You could also just wipe the HD and preset a W7 ntfs partition at the size you want then install W7 then Ubuntu in the the space left open. This last option will leave you with a dual boot without having to modify the MBR.

If it was me I would just reinstall both, starting with W7 first in a set partition size so you don't have to shrink or adjust partition sizes.

---

