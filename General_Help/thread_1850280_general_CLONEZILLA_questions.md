---
title: "general CLONEZILLA questions"
date: 2011-09-26
forum: General Help
---

### Post by liquidmonkey on 2011-09-26
just started using clonezilla and its great!

but some quick questions...

1) the 'savedisk' - this only saves the diskspace used right? meaning if i have a 100gig HDD and only use 20gigs, ONLY 20gigs is saved as an image.

2) is it possible to exclude certain folders? ie, folders that i backup in ubuntu one or dropbox.

3) is it possible to restore an image to virtual box?


thanks!

---

### Post by haqking on 2011-09-26
> **liquidmonkey said:**
> just started using clonezilla and its great!

but some quick questions...

1) the 'savedisk' - this only saves the diskspace used right? meaning if i have a 100gig HDD and only use 20gigs, ONLY 20gigs is saved as an image.

2) is it possible to exclude certain folders? ie, folders that i backup in ubuntu one or dropbox.

3) is it possible to restore an image to virtual box?


thanks!

1. well yeah it only ever clones data. and the image is super small and compressed anyways

2. I dont think so, you can clone a disk or a partition, place your backup or ubuntu one data in a seperate partition if you want

3. yes

---

### Post by liquidmonkey on 2011-09-26
> **haqking said:**
> 1. well yeah it only ever clones data. and the image is super small and compressed anyways

2. I dont think so, you can clone a disk or a partition, place your backup or ubuntu one data in a seperate partition if you want

3. yes



thanks for the reply.
i like your idea of moving the dropbox and ubuntu1 folders to another partition. this would save some time when backing up and reduce the image size.
as it is, the image is 6gigs

is it possible to partition my linux hdd while in linux or is it an absolute must to boot using gparted LIVE?

---

### Post by haqking on 2011-09-26
> **liquidmonkey said:**
> thanks for the reply.
i like your idea of moving the dropbox and ubuntu1 folders to another partition. this would save some time when backing up and reduce the image size.
as it is, the image is 6gigs

is it possible to partition my linux hdd while in linux or is it an absolute must to boot using gparted LIVE?

yeah i would boot to a live CD, the filesystem needs to be cleanly dismounted.

However i would make sure you have a backup of all your data first, and possibly create a clone before partitioning, that way if you accidentally trash things using gparted (if you are not familiar with it) then at least you can just clone things back the way the were ;-)

good luck

---

### Post by liquidmonkey on 2011-09-26
great, thanks for the info :)

---

### Post by haqking on 2011-09-26
> **liquidmonkey said:**
> great, thanks for the info :)

no worries you are welcome.

If you get it sorted the way you want then remember to come back and mark the thread as solved using thread tools, cheers

haqking

---

