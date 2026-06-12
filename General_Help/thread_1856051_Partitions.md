---
title: "Partitions"
date: 2011-10-07
forum: General Help
---

### Post by Drunkfuel on 2011-10-07
I recently upgraded from windows to ubuntu, and one issue I'm currently having, is that in my media libraries, I'm only limited to 10 gigs of data. I have one drive with 2 partitions, and was wanting to know if there was a way to add the partition, or a least increase the allowed storage in the media folders.

Also it seems that Ubuntu does not recognize the partition it is not installed on. For example I cant run programs from it (I've tried Properties/Permissions/Allow executing file as program).

Any help would be great, or if there is a thread that I missed.
Will provide more information on request.

---

### Post by oldfred on 2011-10-07
Welcome to the forums.

Have you added your media partition to fstab to auto mount on reboot? Is partition NTFS or Linux?

Post this

sudo fstab -lu
sudo mount

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Drunkfuel on 2011-10-07
Not sure how to.

The Partition is NTFS

neither of the commands worked.

---

### Post by oldfred on 2011-10-07
Is this by any chance a wubi install inside the Windows partition?

---

### Post by Drunkfuel on 2011-10-07
Oh.. Didn't even think about it. Yes it is. So I guess that the partition is still in windows format?

---

### Post by oldfred on 2011-10-07
The file inside the NTFS partition that is wubi is formated and looks like a standard install, but it still is part of the NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Read wubi from Windows:
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

