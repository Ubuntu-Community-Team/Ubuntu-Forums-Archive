---
title: "ntfs mount won't auto mount nfs does"
date: 2012-04-29
forum: General Help
---

### Post by Swiftjay on 2012-04-29
I'm on ubuntu 12.04.  I have an encrypted home folder, however my nfs mount works fine when I login but my ntfs doesn't.  Is this an issue with ntfs not loading due to my home folder being encrypted?

---

### Post by Swiftjay on 2012-04-30
*bump*

To add more info to this I get this error:

 Apr 30 08:15:11 sourcecode ntfs-3g[2789]: Mount options: rw,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096
Apr 30 08:15:11 sourcecode ntfs-3g[2789]: Ownership and permissions disabled, configuration type 7
Apr 30 08:15:11 sourcecode ntfs-3g[2789]: Unmounting /dev/sda2 ()


My fstab mount is like this:
/dev/sda2       /home/james/WINDOWS     ntfs    defaults        0       0



That has been working fine for me since 10.04 unless I need to change how that operates now then fair enough.


*edit* Resolved, I guess it does have problems with encrypted folders.  I followed the guide here: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)


My fstab is now set to this: 

#Entry for /dev/sda2 :
UUID=DE8444C184449E41   /mnt/WINDOWS    ntfs-3g defaults,locale=en_GB.UTF-8     0       0


closing task, hope if anyone else has issues with this they'll see this post.

---

