---
title: "Software raid on ububtu live"
date: 2006-04-24
forum: General Help
---

### Post by fredrik_human on 2006-04-24
Hi, i'm thinking about building myself a software raided NAS-server to use as fileserver in my network. I am a bit paraniod about loosing my files so i'm going to use raid-level 1, mirroring two 250Gb IDE drives to each other. To save space on the raided disks i thought i might use an ubuntu live cd to boot from. Anyone here who has done something like this or can tell me not to? If so, what are your experienses on the subject, and how did you do it?

//Fredrik, sweden

---

### Post by lha on 2006-04-26
Installing Ubuntu on software raid1 devices is really easy. Just install it. :) In the partitioner, create identical partitions on your drives and set them as 'linux raid autodetect'. Then choose to create md devices and finally select mount points for newly created md devices. If you want to be able to boot with just one drive in case of a failure, you have to install grub on the other drive manually.

Why would you use a live-cd? Ubuntu takes only 2-3GB, server installation needs significantly less. Not much for a remarkable gain in speed.

---

### Post by fredrik_human on 2006-04-27
Well i use NASlite+ at the moment but i want to use something i've configured myself and where i have total control over what services are offered on the network. NASlite+ boots from cd and i thought that doing so would be a good thing in this case too, separating the stored data and the OS on separate mediums. I dont want to boot from the raid-disks, they are supposed to only serve as the place where i store my precious files, so i might as well install some old 3-4Gb disk to run the OS then, instead of using a live cd. 

Thanks for the advice. //Fredrik

---

