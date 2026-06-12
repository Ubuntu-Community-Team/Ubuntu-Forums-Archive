---
title: "How do I rename a partition?"
date: 2009-08-23
forum: General Help
---

### Post by danp824 on 2009-08-23
Hi. :) A friend installed ubuntu for me with 3 partitions on the hard drive. They all have names of "New Volume 1" and so forth, and I'd like to rename them. When I try to do so, I get an error message saying the action is not supported by backend. What does that mean, and how can I go about renaming the drives?
 
Thanks!
 
 
p.s. one more question:  what program can I use to open .rar files, since winrar isn't compatible?

---

### Post by cariboo on 2009-08-23
You have to unmount the partitions in order to make any changes to them. The best way to change the partition labels is to boot from the Live CD and then got System-->Administration-->Partition Editor.

The answer to your second question is to install rar and unrar from the repositories. You can use Add/Remove or SYnaptic package Manager to install them

---

### Post by Rocket2DMn on 2009-08-23
You can change drive labels by following directions here - [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
Note that you can only change labels on partitions that aren't mounted (so you can't change the label of your root partition without the use of a LiveCD, like cariboo907 mentioned).  Although that link mentions USB drives, it is good for internal drives as well so long as you unmount them first.

---

### Post by scouser73 on 2009-08-23
Follow the instructions set out in this tutorial [[COLOR="Red"]**Rename A Hard Drive**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by danp824 on 2009-08-26
Ok.  I installed gparted, and ran Partition Manager.  

I unmounted the drive, and the key icon is gone - but the "label" option is still not clickable - it's gray.  Why might that be? 

(the partitions are formatted with NTFS, if that makes any difference)

---

### Post by drs305 on 2009-08-26
> **danp824 said:**
> Ok.  I installed gparted, and ran Partition Manager.  

I unmounted the drive, and the key icon is gone - but the "label" option is still not clickable - it's gray.  Why might that be? 

(the partitions are formatted with NTFS, if that makes any difference)

In gparted, check View, File System Support, and see if the NTFS row is checked/enabled. If it is not, install *ntfsprogs*:
```

sudo apt-get install ntfsprogs

```

Reopen gparted. If you still can't label the partitions, from the command line use one of the ntfsprogs utilities:
```
sudo ntfslabel <device> <label> 
```		
Example: sudo ntfslabel /dev/sda1 windows

---

