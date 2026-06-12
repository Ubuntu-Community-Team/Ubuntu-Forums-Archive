---
title: "Does GRUB support booting off of a dd image?"
date: 2010-10-13
forum: General Help
---

### Post by dragos240 on 2010-10-13
I'm pretty curious. Because that would be useful. I know a dd image represents an entire hard disk, so I would have to specify a partition. Can it be done?

---

### Post by hangle on 2010-10-15
i just read an interested article that may answer your question. with the dd command you can make an image of the whole disk or copies of particular partitions.  see:

ttp://www.backuphowto.info/linux-backup-hard-disk-clone-dd

 "dd" is much powerful than Norton Ghost. You can use many arguments to control it. In this short article, we only concern on how to backup a whole hard disk or a partition.
Hard Disk Clone

Suppose you have a 40GB hard disk and a removable hard disk whose capacity is 60GB, and you want to backup all the files from the hard disk to the removable disk. With "dd", it is a very easy task. Again, suppose your hard disk's Unix device name is /dev/sda and the removable disk is /dev/sdb. The following command can copy all the content from /dev/sda to /dev/sdb:

dd if=/dev/sda of=/dev/sdb

---

### Post by VMC on 2010-10-15
> **dragos240 said:**
> I'm pretty curious. Because that would be useful. I know a dd image represents an entire hard disk, so I would have to specify a partition. Can it be done?

If you mean boot the *dd* image as in loop-back method, then no. But *dd* can and will backup your grub and anything else in its path. A very powerful command if used correctly.

---

