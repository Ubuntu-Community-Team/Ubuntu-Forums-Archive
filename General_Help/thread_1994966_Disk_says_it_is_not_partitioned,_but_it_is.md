---
title: "Disk says it is not partitioned, but it is"
date: 2012-06-03
forum: General Help
---

### Post by OliverHaslam on 2012-06-03
An odd one this, and it doesn't seem to be affecting anything but I thought I'd ask anyway.

I've got an Ubuntu web and Time Machine server in a VBox VM. I have one virtual drive dedicated to Time Machine, and it works fine.

I've just noticed though that the Ubuntu VM doesn't think the drive is partitioned although, obviously, it is.

Any ideas what's going on?

Screenshot attached.

Cheers.

---

### Post by oldfred on 2012-06-03
Someone posted before with a drive that was formated but not partitioned. It just is one massive storage. Not sure what issues that causes as many tools expect partitions, but someone did post it works and save the space (not really much) taken by partitioning. Is this what you have?

Not really possible to revise as you do not have partitions and just writing partition table & data will overwrite parts of your data, so if you want to convert to partitions you have to totally backup, partition & restore data.

---

