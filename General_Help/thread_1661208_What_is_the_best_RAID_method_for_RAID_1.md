---
title: "What is the best RAID method for RAID 1?"
date: 2011-01-06
forum: General Help
---

### Post by Mahler122 on 2011-01-06
Hi,

I'm currently using a dual boot windows xp/ ubuntu 9.10 set up. My motherboard came with an onboard software RAID implementation (NVRaid, don't remember the motherboard exactly, will post those details later), and I have used this for some time with 2 drives in RAID 1. I was able to get it working just fine in both windows xp for which it was designed, and ubuntu which took a bit of work.
When one of the drives failed, it caused a whole bunch of problems with the way that the storage controller was configured, and I have only just now restored my system to operation without the RAID. I now have the drive which hasn't totally died attached as an external drive.

What I'm wondering is what would be the best way to set up a RAID 1 array in an OS agnostic manner. i.e. would it be hardware? if so what controller card would you recommend? or would it be software if so what motherboard, or perhaps what extra software would I need?

I would like to avoid the problems that I ran into this past time, but I'm willing to entertain the idea that I was just an idiot about setting it up.

---

### Post by Grenage on 2011-01-06
While I'm not a fan of software RAID, you'll need to consider the price if going for a hardware option.  The cards aren't cheap - usually £100-120 minimum.

---

### Post by pricetech on 2011-01-06
If you want OS independence, hardware RAID is the only way to go.

---

### Post by SoFl W on 2011-01-06
I purchased hardware based RAID drive units on-line for redundancy storage.  I have a "Sans Digital" unit that I currently use and it seems to work well.   The problem with raid units is you don't know if they work until one drive fails.  

If you are using it for redundant back-up remember corruption can be copied to the other drive, still perform regular external backups.

I read a on-line review, some guy was thrilled with his 1T drive RAID.  He partitioned it into two partitions and said he was using it to speed up data access.

---

### Post by dcstar on 2011-01-07
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

