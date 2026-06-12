---
title: "Raid Advice"
date: 2010-02-28
forum: General Help
---

### Post by FeraTech on 2010-02-28
I recently set up a Raid1 system with LVM. After much struggling I came on this setup which actually works well.

I have two 1500gig drives. I made two full 1500gig partitions bootable and set them up as Raid1. Then I made LVM partitions for root / and swap.

Is there a better way to partition this kind of setup with this much space? I've been looking at a lot of posts having separate /var and /home partitions. Is this necessary? Will it increase performance?

Any input would be greatly appreciated. I've been looking through a lot of documentation and haven't come across a straight answer.

---

### Post by blair on 2010-02-28
I did something slightly different to simplify things. I have a basic ~80GB drive that is my "main" drive. It contains the OS, and partitions for /home, /var, /tmp all that. A standard generic install. I keep zero personal data on that drive and don't care if if ever dies as I will simply install the newest, latest Ubuntu version at that time. 

I installed 2 1TB drives in a RAID1 config so they mirror each other and put ALL my data on there. 1 TB sounds like a lot but with videos, photos, MP3 and lossless FLACs, it is filling up fast. If one drive ever dies, I have a 100% identical backup.

---

### Post by cjhabs on 2010-02-28
From my experiences with ubuntu & other *nix oses, I would say that you want a root, swap and home partition as a minimum (optimum for me).

That way, when you update or rebuild the OS, you don't touch your data on /home. 
You want swap to be at least equivalent to the amount of ram you have to support power management.

For installs that do a lot of printing I have also configured a separate /var, where temp print files go (I think this is also true of Ubuntu - not positive)

Some people have a separate /boot for grub - I have a simple single boot scenario so I don't bother.

HTH

---

