---
title: "Accessing my Windows 7 files from ubuntu 12.04"
date: 2012-08-12
forum: General Help
---

### Post by Highnotlow on 2012-08-12
I've installed Ubuntu 12.04 alongside Windows 7, and I was wondering how can I access my videos and music and pictures from Ubuntu?

---

### Post by oldfred on 2012-08-13
Welcome to the forums.

Linux has a NTFS driver and you can directly mount a Windows partition from Nautilus. It may just show as the partition size in left panel, unless you labelled your partition. I like to label partitions I do not mount with fstab, so I have a name that I understand. You can add labels with Disk Utility or gparted.

The NTFS driver though allows full access to all the normally hidden files & folders that Windows hides. I used to always unhide them in Windows but then click and slight move mouse while clicking and move a file or folder corrupting system.  So you do have to be careful. Also too many writes into the NTFS partition seems to disagree with Windows so make a Windows repairCD to allow you to run chkdsk or make other repairs.

Do not hibernate Windows and try to write into the Windows partition as then the hibernation may get corrupted and file will not be saved.

Often best to create a separate shared NTFS partition for any data you may want to share and set the Windows system partition as read-only.

If you want specific permissions you have to set those by permanently mounting a NTFS partition by using fstab.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

more info and details 
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

