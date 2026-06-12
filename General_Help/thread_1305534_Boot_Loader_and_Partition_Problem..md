---
title: "Boot Loader and Partition Problem."
date: 2009-10-29
forum: General Help
---

### Post by 1234blizzard on 2009-10-29
So being to noob that I am, I wanted to install windows 7 on my existing hard drive with Ubuntu 9.10. I booted into the windows 7 install and realized I couldn't partition my hard drive so I went back into 9.10 and tried partitioning. For some reason it didn't let me so I decided to use my Ubuntu 9.04 Desktop Cd to partition it, install ubuntu 9.04 and just wipe it when installing windows. 

So after this long process, I end up getting a error message that I can't install windows even though I formatted the hard drive to NTFS. Well, seeing that I failed, I had to reinstall Ubuntu 9.04 in the free space because the boot loader wouldn't load up. After this, I now have 2 partitions one with 9.04 and another with 9.10. I want to get rid of 9.04, merge the space back into 9.10 and reinstall the boot loader.

Please Help!

Thanks in Advance, (and for reading all that)

---

### Post by alphaniner on 2009-10-29
One thing I've noticed is that Windows will refuse to install to an NTFS formatted partition if the partition is not ID'd as HPFS/NTFS.  If you partitioned and formatted with gparted, though, this probably isn't the case.

Not sure what the best course of action is for you.  A screenshot of gparted showing how your partitions are laid out, or the output of **sudo fdisk -l** would probably help your cause though.

---

