---
title: "Hybrid RAID - possible?"
date: 2012-06-04
forum: General Help
---

### Post by stueng on 2012-06-04
Products such as Synology offer something called Synology Hybrid RAID

[http://www.synology.com/us/products/features/RAID.php](http://www.synology.com/us/products/features/RAID.php)

This RAID type allows you to make best use of your disks available by using all the disk space available as long as at least two disks share the same increased size where a typical RAID setup would simply "throw away" the extra space

I would like to build a NAS with 4 disks available. I will begin by populating it with 3 X 3TB to give me 6TB usable. By the time I have filled this 6TB I imagine that 4TB disks will have come down in price, so at this stage I would add a 4th 4TB disk to give me an additional 3TB of space. When I next run out of space I will change one of the original 3TB disks with a 4TB disk giving me an additional 1TB of space. 

This is not possible with a typical RAID configuration, only with these "hybrid RAID" types

I am wondering if I can acheive a similar "hybrid RAID" with Ubuntu? or another linux distro?

---

### Post by Cheesemill on 2012-06-04
Greyhole may do what you're after.

[http://www.greyhole.net/](http://www.greyhole.net/)

---

### Post by rubylaser on 2012-06-04
Here are a few solutions that will also do this...

1. [Unraid]("http://lime-technology.com/")
2. [mhddfs]("http://romanrm.ru/en/mhddfs") + [Snapraid]("http://snapraid.sourceforge.net/")
3. [Flexraid]("http://www.flexraid.com/")

mhddfs + Snapraid is the only free solution from my list that will do what you're asking for. But, it does not provide realtime parity so you'd need to schedule the snapshot via cronjob. This is not a big deal if you're planning to use this as a media server as typically the content on the server is pretty static throughout the day.

---

