---
title: "Repartitioned The Wrong Drive"
date: 2011-07-31
forum: General Help
---

### Post by ZombiiBite on 2011-07-31
I wasn't paying close attention when I partitioned the drive and like an  idiot I chose my external and used up quite a bit of it how and is  there a way to change it to my internal.  Please HELP!

---

### Post by tigerlxxv on 2011-08-01
You may find that this is an easier fix than you suspect. If the drive that you're re-partitioning is the one that you're booting from, you'll need the LiveCD to do it, but it's pretty straightforward. Just boot from the LiveCD, click the "Try Ubuntu" button, and *don't* open any of the drives, this will make sure that they aren't mounted. Once it's running, go to the System menu on the top panel, and go to Administration. Open Gparted from there, and track down the drive you're after. Before you go to all this, though, make sure you've defragmented the drive, as a badly fragmented drive can end up with bits of the files chopped off when you take away the end of the partition to make another. While you're in Gparted, you can also rejoin the two partitions on your portable drive, so that you have your free space back. Good luck, and post back here if anything goes awry. Or even if it works :)

---

