---
title: "Acer Aspire One with issues"
date: 2010-04-28
forum: General Help
---

### Post by SeanCly10 on 2010-04-28
Hi all,

Got a knotty problem I hope that someone can help with. Here's the situation.

My AAO ZG5 laptop is about a year old right now, and an apparently common problem with the internal SSD has manifested itself: some sort of damage in the first 8 MB or so of the drive. I first found it out when I tried to install UNR 9.10, and the install locked up at 70% of the partitioner.

Googling for a bit brought me to this page: [http://gparted-forum.surf4.info/viewtopic.php?id=13825]("http://gparted-forum.surf4.info/viewtopic.php?id=13825"), where the intrepid gentleman InfuriatingSSD hammered out a way to do the install successfully despite the same issue. For him, all went well eventually, but my following his instruction only went as well as the reboot, at which time I get to where GRUB2 is supposed to kick in and all I get is an eternally blinking cursor.

I know that this must be a GRUB2 issue, since booting again with the LiveUSB lets me view the new install in all its' glory. Plus, on one occasion where I ran 'grub-pc' and somehow managed to install GRUB2 to the USB stick itself, the little thing did boot successfully.

So, here's where I sit. I know that something in the configuration of GRUB2 is stopping me, I just don't know what. GParted on the drive, /dev/sda, reads like this: the first 196 MB is free, unallocated space; /dev/sda1 is a 204 MB ext3 partition where I believe GRUB2 is placed; /dev/sda2 is a 7.12 GB extended partition containing /dev/sda5, which is a 6.77 GB ext4 partition housing the OS itself, and /dev/sda6 which is 361 MB swap space.

Further Googling has netted me several tutorials on GRUB2 configuration, but thus far I haven't had any luck getting it to boot on its' own. Would a kind soul with experience whipping a recalcitrant GRUB into shape give me some direction to fix my poor little netbook?

---

