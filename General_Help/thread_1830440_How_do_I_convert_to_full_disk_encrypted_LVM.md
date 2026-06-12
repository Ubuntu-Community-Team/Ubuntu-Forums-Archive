---
title: "How do I convert to full disk encrypted LVM?"
date: 2011-08-21
forum: General Help
---

### Post by stuartbh on 2011-08-21
Hello everyone!

Originally intending to leave in tact a WD "utilities partition" on a WD 750GB USB HD, I enunciated an installation of Ubuntu 11.04 using manual partitioning (in the end I blew the WD utility partition away, realizing the software on it was stale and downloading the newer software was the way ahead anyway).

Now it interests me to convert my instantiation of Ubuntu 11.04 onto an encrypted LVM partition absent the requisite of conducting a fresh installation as I have invested quite a bit of time installation software, downloading updates, configuring it as desired, etc...

Also, are there choices I have as to what encryption mechanism is going to be used in having full disk encryption?

The current formatting is as follows hereupon:

Primary Partition #1 - 10GB (Ubuntu 11.04)
Primary Partition #2 - 10GB (reserved, no installation or data)
Extended Partition #1
   1) 650GB of encrypted ext4 space (about 4-5GB used)
   2) 64GB - formatted as NTFS (no data on it yet)

Scope/Caveats
-------------

1) Preservation of the Ubuntu 11.04 installation

2) Preservation of the 5GB of data on the encrypted partition (though perfectly willing to move it, even to an unencrypted partition temporarily)

3) Presuming I can achieve #1 and #2, I am willing to blow away, resize, delete, etc... the partitions as appropriate

4) I have a bootable DVD drive and a bootable DVD media copy of Ubuntu 11.04

5) Eventual planned layout for the WD 750GB external USB HD

   a) One large encrypted root filesystem
   b) One unencrypted small (300MB?) /boot partition (unless avoiding an unencrypted /boot is possible, is it?)
   c) One 64GB NTFS partition capable of being mounted if the internal HD with Windows XP is booted up


Thank you in advance.


Stuart

---

