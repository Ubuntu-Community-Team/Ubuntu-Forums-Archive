---
title: "RAID-10 rebuild"
date: 2011-09-15
forum: General Help
---

### Post by fixerdave on 2011-09-15
bit of a cross-post I guess, started here:
[http://ubuntuforums.org/showthread.php?p=11252347#post11252347](http://ubuntuforums.org/showthread.php?p=11252347#post11252347)
no answer, and it's a little more serious now.

I'm running a SATA2 raid-10 array built using Intel Rapid Storage Technologies pre-boot setup, part of the Acer system I'm running. It works just fine. I left my OS disk alone and just threw an extra 4 drives in the system, used the pre-boot Intel menu to configure them as RAID-10 and installed Ubuntu 11.4 on the single drive. Nothing fancy, no dual boot, no extra raid packages installed, nothing. In Ubuntu's Disk Utility, I just picked the raid drive and formatted it... done. The raid array comes up a little odd in Ubuntu proper, showing 2 of them in the places menu, only one of which works, and the order is a little random on each boot. But, it works just fine.

The other day, I start getting SMART events (the computer, not me... I'm still waiting for those). One of the raid drives was failing. No problem, I have a spare, so I threw it in. The Intel pre-boot setup declares the array as "rebuilding in the OS" and so I boot into Ubuntu.  

So, just how to I get Ubuntu to rebuild the mirror part of my Raid-10 array?  I thought it was doing it yesterday... lots of hd activity that eventually stopped after a few hours.  But, on boot today, the Intel pre-boot config still says "rebuilding..."  There's nothing in this pre-boot menu that lets me initiate a rebuild.

Is there a utility, cl or gui, in Ubuntu that will show me the status of this array?  Is there a way to force that rebuild?  Having just had a failed drive, I'm a little keen on keeping that mirror part working for the next time.

    David...



Solution:

sudo dmraid -sa    to get a report on the array
sudo dmraid -rebuild "name from above"   to rebuild it.

---

