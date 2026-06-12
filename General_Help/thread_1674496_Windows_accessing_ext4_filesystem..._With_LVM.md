---
title: "Windows accessing ext4 filesystem... With LVM"
date: 2011-01-24
forum: General Help
---

### Post by Tynach on 2011-01-24
Well, I've installed [Ext2Read]("http://sourceforge.net/projects/ext2read/") and it can read my /boot partition (sda5), which is a normal partition.

However, the rest of my OS is on an LVM setup (one entire drive, along with a partition from another drive merged), and I would like to access it while I am in Windows. Is there a way to do this?

Ext2Read does detect a 'second' ext4 partition on sdc2, but it won't open.

I only have two drives. Why is it saying anything about sdc2? Shouldn't that be sdb2? I's confus.

---

