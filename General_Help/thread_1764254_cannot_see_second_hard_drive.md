---
title: "cannot see second hard drive"
date: 2011-05-21
forum: General Help
---

### Post by soulcat on 2011-05-21
hi 

installed xbuntu 10.10 cannot see my secondary drive which is fitted internal not external usb


help

---

### Post by Rebelli0us on 2011-05-21
It's probably not mounted. "Mount" it!

---

### Post by soulcat on 2011-05-21
hi

how do i do that, previously used ubuntu 10.10 & that picked it up

regards

---

### Post by oldfred on 2011-05-21
Are you sure you do not see it? If often is in the left panel of Nautilus as 221GB or whatever size it is. Or if you have a label on it, it will show by the label. Oops missed that you have xubuntu, not sure what file system you then have.

But all Ubuntu's use the same mounts. You do not mount drive, but the partitions created on the drive.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Aboe link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

If it is a NTFS partition and needs chkdsk Ubuntu will not mount it to prevent damage that chkdsk may then not be able to correct.

---

