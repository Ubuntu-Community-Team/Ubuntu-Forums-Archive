---
title: "Partitioning challenge"
date: 2011-03-30
forum: General Help
---

### Post by texas.chef94 on 2011-03-30
I was able to create and install data partition. Do not know why media was the ID in label but that is not my question.
Created another partition labeled Recipes and applied the same code but went to places where Data partition is displayed, but no access to other so I must have done it incorrectly. Two attachments are to help you help me I hope and thanks.

---

### Post by oldfred on 2011-03-30
Did you do this after editing fstab?

mount -a

If no errors it should just come back and everything is mounted. Do not reboot if errors as you may not be able to. Resolve errors first.

I prefer to use UUIDs or labels to mount in fstab and to make mount points be names rather than partition numbers. I have mixed up partition numbers and caused myself much grief. Some times I use label and mount point with same name but use identical capitalization or you can get very confused.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I do not use FAT anymore, but just NTFS. FAT is ok for small partitions or where required for external devices. But you cannot copy a file over 4GB to a FAT partition (When I did it, I got no error message and file was just truncated). Also large FAT partitions can take forever to run chkdsk on, NTFS is slow also, but faster than FAT.

---

