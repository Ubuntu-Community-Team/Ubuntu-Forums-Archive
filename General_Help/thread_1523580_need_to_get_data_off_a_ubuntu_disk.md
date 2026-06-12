---
title: "need to get data off a ubuntu disk"
date: 2010-07-03
forum: General Help
---

### Post by ulao on 2010-07-03
I figured I could just go in to my Kubuntu desktop and look at the drive. but it has only a lost and found and grub folder with a few files on the root named config-[version]-server (note this is a SCSI). Guessing I'm looking at the boot partition huh?

so how do I mount the other partitions?

When i do a fdisk -l I see 3 sdb 1,2,3 (2 and 3 are large, 1 is my boot partition) but when mounting them I get wrong fs type. I was sure its ext3 ( also tried 2 and 4 )? I just left the default 7.04 fs when I installed it. I'm able to put it in my desktop and my server but for the life of me I can figure out how to get at the data.

---

### Post by Leppie on 2010-07-03
try doing a fsck on the partitions.

---

### Post by ulao on 2010-07-03
Well I finally got to the drives with recovery. I was able to tar all important data and use smbclient to send to another computer. 

I will try the check disk now that I'n finally in. Before I do this can any one suggest good directors to put? 

I did my www folder.
will do my etc folder
any others?

---

### Post by ulao on 2010-07-04
so how does one do a fsck. I'm told it will cause "sever" damage if I do this while mounted?

---

### Post by Leppie on 2010-07-04
yes, you have to unmount the partition you want to check first.

---

