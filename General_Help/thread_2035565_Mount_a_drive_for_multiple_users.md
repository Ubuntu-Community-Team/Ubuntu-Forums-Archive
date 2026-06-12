---
title: "Mount a drive for multiple users"
date: 2012-07-30
forum: General Help
---

### Post by Tuxedo Mask on 2012-07-30
I have a second hard drive with a pair of NTFS filesystems which mount to directories in my home folder with full access. I'd like to let another user - who also has admin access - read the directories with the same permissions that I have. What would be the most effective way of doing this? Thanks.

---

### Post by oldfred on 2012-07-31
Because it is NTFS, it only has the default ownership & permissions you set at mounting. 

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://opensuse.swerdna.org/susentfs.html](http://opensuse.swerdna.org/susentfs.html)
Auto mount NTFS Partition
[http://ubuntuforums.org/showpost.php?p=7342606&postcount=10](http://ubuntuforums.org/showpost.php?p=7342606&postcount=10)

You just do not want the UID 1000 setting as that is just the first user.

Older example, UUIDs now preferred as in examples in links above.
What this will do is mount the partition with owner = root but with read / write permissions ( umask=007 ) granted to all local login users ( gid=46 ).
 /dev/sda2 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46,windows_names 0 0

---

