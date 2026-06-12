---
title: "Resizing ext4 partition"
date: 2010-11-20
forum: General Help
---

### Post by jmki1 on 2010-11-20
I clean installed Ubuntu 10.10 by shrinking my Windows 7 partition slightly.  Now that I want to expand my Linux partition, I shrunk my Win 7 partition from Windows OS.  From Ubuntu, the partition manager shows /dev/sda1 contains the Win 7 and unallocated partition.  /dev/sda2 contains the Linux and swap partitions.  I can't seem to expand my Linux partition (ext4) in sda2 with the unallocated space in sda1.  I also can't shift the unallocated space in sda1 to sda2.  Any idea how to expand my main Linux partition with the unallocated space?

---

### Post by Garandir on 2010-11-20
You will need to boot from the LiveCD you installed with, and you can use Gparted from there.

---

### Post by coffeecat on 2010-11-20
It sounds as though sda2 is an extended partition. Apart from booting from the live CD, you need first to swapoff the swap partition. That is, right-click on it and choose 'swapoff'. Then resize your sda2 extended partition. Only then can you resize your Ubuntu root partition.

---

### Post by garvinrick4 on 2010-11-20
You can not do anything while a partition is mounted, that is why live cd.
Install cd and use Try Ubuntu is a Live cd.

---

### Post by jmki1 on 2010-11-20
Thanks (@all, @coffeecat).  Just needed to swapoff, resize sda2, then resize sda5.  Back in 9.04 when I used ext3 my Windows partitioner could take care of it all.

EDIT: Ignore that pic, didn't realise it had uploaded.  This can be closed.
EDIT2:  Wow, that's going to take a while (est 1hr for 117GB).

---

