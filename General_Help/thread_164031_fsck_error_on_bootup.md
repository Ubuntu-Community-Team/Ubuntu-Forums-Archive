---
title: "fsck error on bootup"
date: 2006-04-22
forum: General Help
---

### Post by sbddude on 2006-04-22
on booting up I get the following error:

fsck.ext3: No such file or directory while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem....


* fsck failed. Please repair manually.

CONTROL-D will exit this shell and continue system startup.

How can i fix this, or at least hide the error message so it can boot uniteruppted without having to hit ctrl-D?

---

### Post by joft on 2006-04-22
Hi,

the partition /dev/sda3 belongs to isn't your root ( / ) partition, right? And after booting up you can access all your data? Are you aware of such a partition (sda3 = third primary partition on first SCSI drive)? No?

Then I would say, that you've got a "false" entry in your /etc/fstab file, referring to a partition (/dev/sda3) which does not exist.

---

