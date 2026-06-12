---
title: "USB External Hard Drive - Ext2 or Ext3"
date: 2011-07-23
forum: General Help
---

### Post by dodle on 2011-07-23
I have formatted an 80gb external hard drive to Ext3, but [this article](http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/) recommends formatting external drives to Ext2. Is there a reason I should use Ext2? The Lost+Found directory of the Ext3 file system is kind of annoying to look at. I don't want to format to Ext4 because there is no driver for Windows yet that allows read/write... I think. At least I haven't found one yet.

---

### Post by 2F4U on 2011-07-23
The main reason for choosing ext2 over ext3 on an external drive is probably the journaling, which ext2 doesn't have. If the drive is cleanly unmounted there is no need for journaling.

---

### Post by vanadium on 2011-07-23
Journaling file systems are less prone to severe file system corruption, which is why they are generally preferred. ext2 may be recommended on flash drives because flash drives can be written to a limited number of times. ext2 does not need as much writes as a journalling file system.

---

### Post by bodhi.zazen on 2011-07-23
> **vanadium said:**
> Journaling file systems are less prone to severe file system corruption, which is why they are generally preferred.

That is not strictly true. A journal helps with data integrity in the event of power loss, but that is for data that is in the ext3 journal, it the data that is cached, and not yet written to the disk, ie any changes in the last 30-120 seconds or so, not they entire file system.

The journal is a buffer for data that is being written to the disk, not the entire file system.

See : 
[http://www.ibm.com/developerworks/linux/library/l-journaling-filesystems/](http://www.ibm.com/developerworks/linux/library/l-journaling-filesystems/)
[http://www.redhat.com/support/wpapers/redhat/ext3/](http://www.redhat.com/support/wpapers/redhat/ext3/)

> ext2 may be recommended on flash drives because flash drives can be written to a limited number of times. ext2 does not need as much writes as a journalling file system.

That and ext2 does not have the overhead of the journal and is a reasonable choice.

---

### Post by vanadium on 2011-07-23
I stand corrected on the first point indeed, thanks.

---

### Post by bodhi.zazen on 2011-07-23
> **vanadium said:**
> I stand corrected on the first point indeed, thanks.

It is an esoteric point and it was not my intention to nitpick. I agree EXT2 can be a good choice for removable devices.

---

