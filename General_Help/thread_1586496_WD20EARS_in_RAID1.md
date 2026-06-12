---
title: "WD20EARS in RAID1"
date: 2010-10-02
forum: General Help
---

### Post by calvinchu on 2010-10-02
I recently installed a pair of WD20WARS drives and created a RAID 1 array with Perc 5/i raid card. I would like to create a single ext3 truecrypt encrypted partition with the whole drive (2TB). It is for data storage only as my OS are installed in a separate disk.

As the drives are of 4k sector size, from other post I knew that I need to align the partition such that it fits 4k sector.

However, when I use GParted to create the partition, there is no option for the offset. So I need to use the fdisk command to create and align the partition before creating the truecrypt volume ? Is it necessary to do so ? Seems Truecrypt will re-create the partition during volume creation.

Also, Truecrypt 7.0 start to support 4096 sector size, can I assume Truecrypt will handle the alignment automatically ? How to check the align of a Truecrypt volume ? fdisk doesn't recognize Truecrypt encrypt partition.

Thank you very much !

---

### Post by srs5694 on 2010-10-02
I know nothing about your specific RAID controller card, and very little about TrueCrypt; however, I would not recommend assuming that either one will automatically fix partition alignment issues. I'd make sure that the partitions you create are properly aligned. This can be done in several ways, but it's easiest to use the latest partitioning software available. Check [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) on the topic for some advice for several partitioning programs; but be aware that partitioning programs' options for handling alignment are changing rapidly, so applicability of this advice depends on the specific version you've got.

---

