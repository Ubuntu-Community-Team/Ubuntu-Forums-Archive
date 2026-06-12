---
title: "chown not working on external NTFS drive"
date: 2010-02-27
forum: General Help
---

### Post by DeMus on 2010-02-27
Hi,

I have an external drive which is parted into two partitions:
1) ext4, with filesystem ext4 which I use for backup
2) NTFS with filesystem NTFS

Since I re-installed jaunty the NTFS partition is owned by root. Whatever I do to make it change, it doesn't work. I used:
sudo chown jan:jan NTFS
sudo chown -R jan:jan NTFS

Still it says the owner is root and also the group is root.
What else do I need to do to make me owner of this partition?
The fileproperties say: drwxrwxrwx
Still the partition is read only for me.

In ntfs-config it says:
"Enable write support for external drive"

What else can I do?

---

### Post by oldfred on 2010-02-27
NTFS does not support any linux properties. You cannot chown or chmod NTFS.

My internal NTFS partition is owned by root and I do not have any issues reading & writing to it, but I mount in fstab.

How are you mounting it?

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

My fstab entry:
# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0

---

