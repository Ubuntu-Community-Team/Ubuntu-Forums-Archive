---
title: "striped drive problems"
date: 2010-12-19
forum: General Help
---

### Post by nevans on 2010-12-19
OK I have been using Ubuntu for a while now (7.04) and have run into an issue that I need help on.  While I have used Ubuntu for a while, the depth of my understanding is in constant need of upgrading  :)

I installed Ubuntu 10.04 and AVLinux on an appropriately partitioned 80 gig hard drive.  All works well. My computer has 4 250 gig hard drives and an intel 82801 host controller.  I did partition the drives individually but I would like to set these drives up in raid 0.  Disk utility sees 4 251gig drives underneath the intel 82801 sata host adapter.  gparted sees 4 individual 233.76gig drives and no sata host adapter.  I would like to have these drives striped with 200gig of NTFS and the rest as ext3.  How can I do this?

Thanks

Neal

---

### Post by ronparent on 2010-12-19
I think your problem is the same as one as in a post I just answered. To make a long story short, if you are using 10.04 or 10.10, you need to install kpartx ('sudo apt-get install kpartx') to enable gparted to read the raid partitions. The problem has supposedly been fixed upstream.

---

### Post by nevans on 2011-01-04
OK sorry,  I went out of town suddenly but now am back.  I installed kpartx but this doesn't seem to have made any changes. I still see just the separate drives and no controller.  Thanks in advance.

---

