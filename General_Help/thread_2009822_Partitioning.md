---
title: "Partitioning"
date: 2012-06-25
forum: General Help
---

### Post by Musicmaker384 on 2012-06-25
A while back I had a problem with Windows (who doesn't). The problem was bad enough for me to uninstall it and install Ubuntu as the primary OS, even though at the time I had a true dual-boot of the two. I'm now trying to reinstall Windows 7, and I need to make a new partition to do it. GParted won't let me and I don't know why. I have one primary partition, one logical and 3gb of swap space. I've searched here on Ubuntu Forums and Google and can't find anything related to this problem. If someone could give me some advice on how to fix this, I'd appreciate it. Also, if it's not too much trouble, I'd like advice on what I have to do with the grub menu since I don't have an installation of one with only Ubuntu installed.

Thanks.

Edit: I can't resize partitions either.

---

### Post by Foxheadz on 2012-06-25
In order to partition a harddrive you have to unmount it, the only problem is you can't do that while running an os off that hard drive. That being said, all you have to do is boot into a liveCD and run GParted from that.

---

### Post by Mark Phelps on 2012-06-25
Also, you DO have a GRUB menu installed -- you're just not seeing it because the default is to NOT show it if only one OS is installed.

When you do the partitioning, create an NTFS partition for Win7, but when you boot from the Win7 DVD to do the install, be SURE to use the option to reformat that partition.  Win7 works better if you let it do its own partition formatting.

---

### Post by Musicmaker384 on 2012-06-25
Alright. I'll do that once I grab my live cd from home. Thanks for the info on the grub too. Also... I did try using google. The search yielded no usable information. =] Sorry for asking a dumb question.

---

