---
title: "df doesn't agree with baobab (Disk Usage Analyzer)"
date: 2010-08-20
forum: General Help
---

### Post by thekwill on 2010-08-20
Every time I log in recently I've been getting low disk space warnings. I have lots of big files (virtual machines, dvd backups and movies), I've been removing them, clearing the apt cache, etc, etc, but I'm still getting warnings after deleting GBs of stuff!

I've tried using df and baobab (Disk Usage Analyzer) to find out what more I can remove and was suprised to see them reporting different free space:

When I open DUA it says I have 16.5 GB free. When I run df --si from the command line it says I have only 142 MB free. How can I figure out where the missing space is being used?

My partitions are fairly simple, I have one ext4 partition for both system and user data, and one extended partition for swap. The swap partition is 7.7 GB, so that doesn't account for the missing space.

---

### Post by silverglade00 on 2010-08-20
Is it maybe in your trashcan folder?

---

### Post by thekwill on 2010-08-20
I have gone through and emptied all my Trash folders, including /root/.local/share/Trash - but thanks for checking!

Also, I have run these apps with sudo just to be sure, the results are the same.

What confuses me is why the two apps report differently. Ubuntu obviously believes df :)

---

### Post by thekwill on 2010-08-23
I installed and ran xdiskusage, which revealed a folder called inodes, approx 14.5 GB. [http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode) This accounts for most (but not all) of the missing space.

Any ideas on how to reduce the size of inodes?

I've logged a bug for Baobab not showing/counting the inodes folder - [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/622671](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/622671)

---

### Post by DaithiF on 2010-08-23
Hi,
I believe the diskusage 'inodes' value is just a subtraction of the known disk usage from the filesystem size, ie. its just a plug value rather than an actual file/folder that is consuming space. 

For such a large value it sounds to me like this issue:
[http://ubuntuforums.org/showthread.php?t=1251827](http://ubuntuforums.org/showthread.php?t=1251827)

i would suggest running the lsof command mentioned in that thread to see if you have any open but deleted files.

---

