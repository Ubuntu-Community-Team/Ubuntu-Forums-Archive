---
title: "Second drive is NTFS, can i convert it?/Mount it on boot easily?"
date: 2010-01-05
forum: General Help
---

### Post by shamusl on 2010-01-05
When I installed Ubuntu, my Windows partition was dead, so I installed ubuntu on half the drive thinking I would reinstall windows at a later time, but now I don't want to. My second drive unfortunately is 750gb and is full of data in NTFS, which requires authentication every time I boot my system. 

Is there some way to convert my second drive from NTFS to EXT4 without deleting all the data? Or is there some way to mount the second drive on boot, skipping authentication?

---

### Post by michy99 on 2010-01-05
There is no way to reformat to ext4 without losing the data. You would have to backup the data and then restore after the format.

You can, however mount the disk at boot as it is now. All you have to do is add it to your /etc/fstab file.

---

### Post by michy99 on 2010-01-05
For a fairly easy way to automount, see this:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by dcstar on 2010-01-05
> **shamusl said:**
> 
.........
Is there some way to convert my second drive from NTFS to EXT4 without deleting all the data? Or is there some way to mount the second drive on boot, skipping authentication?

The **pysdm** package will allow you set up the automatic mounting of a partition.

---

### Post by shamusl on 2010-01-05
> **michy99 said:**
> For a fairly easy way to automount, see this:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

Thanks, that worked great.

---

