---
title: "What's involved with replacing a failed HD on a software-RAID setup in Ubuntu?"
date: 2010-03-07
forum: General Help
---

### Post by diablo75 on 2010-03-07
I've been looking into building a rack-mounted NAS using Ubuntu to run a software-based RAID setup instead of paying more for a hardware based solution using a controller card.  Looking over this little guide on how to set things up:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Things appear to be pretty simple.  But I have two questions.

First, it says that "/boot filesystem cannot use any softRAID level other than 1 with the stock Ubuntu bootloader. If you want to use some other RAID level for most things, you'll need to create separate partitions and make a RAID1 device for /boot."

Does this mean if I wanted to create an array with 4 drives running RAID 5, I would have to create a /boot partition on a fifth drive?  Or just start by creating a tiny boot partition manually, then manually create all the rest of the partitions (which would seem to go beyond the scope of the guide above because it has you do everything in a "Guided partitioning" fashion).

Second question:  Once the RAID is up and running, what typically happens when one of the drives fail?  How are you alerted about the drive failure?  What steps are involved with replacing the drive and rebuilding what the bad drive had on it within the new replacement drive?

Sorry for the dumb questions but this stuff is very new to me.

---

