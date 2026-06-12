---
title: "ubuntu and windows same /home folder"
date: 2010-12-15
forum: General Help
---

### Post by othiena on 2010-12-15
i know it is possible to put ubuntu's /home folder and windows 7 /users folder on a separate drive. But is it possible to have an account on windows and ubuntu use the same home folder?


P.S. i want it to use the same Documents folder, same Desktop folder, same Downloads folder, etc.

---

### Post by oldfred on 2010-12-15
You cannot share /home as that is a Linux system partition that has to have Linux permissions & ownership. Windows will not read the Linux system.

But you can share data. Create a separate NTFS partition and put all your data into that. I use a NTFS shared partition for my Firefox & Thunderbird profiles, so I have all the same Firefox (except a few addins) & Thunderbird in both XP & Ubuntu. 

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I link data folders into my /home from an ext3 /data partitions. You can do it also from NTFS.

With NTFS you have to set your default permissions as part of the fstab entry:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by cracker89 on 2010-12-15
Well said Sir!

---

### Post by nonly1n on 2011-07-18
Thinking about this I don't find it impossible, 

keeping the same user name and having home mount in the windows partition user folder (C:\Users\) it is very possible, you could theoretically have everything the same either side, its not much a permission and rights thing but just a lot of unnecessary work with enough trial and error to just find a solution that works on both sides

---

