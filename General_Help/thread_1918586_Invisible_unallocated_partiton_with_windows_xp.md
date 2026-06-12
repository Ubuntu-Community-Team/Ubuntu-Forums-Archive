---
title: "Invisible unallocated partiton with windows xp"
date: 2012-02-01
forum: General Help
---

### Post by patriqo on 2012-02-01
Welcome
I recently installed Ubuntu 11.04 near Windows XP. I chose the other solution and I made swap and ext4 partiton. Windows was on NTFS partiton and I thought that it will still work even after such action. It moved to unallocated. I had installed ubuntu before and nothing happened like that. I will install Windows 7 anyway so I don't care about the system. I just want to get the data back. But Ubuntu doesn't see unallocated unless I open it with GNOME Partition Manager. I don't want to expand the partitions that I have because there is a probability that I will lose data during the process. I thought about cloning the disc. What  do you think about it. Then I can experiment with partitions. I also checked many sites and there is nothing that can help me in 100%. Please help me. 

 Patrick
  If there is anything you need to help me, just ask.

---

### Post by CatKiller on 2012-02-01
If it's unallocated then there's no partition there. Sounds like something went wrong with your partition table.

There are tools that will scan the drive and guess where the partition boundaries should be based on the data structures, although I can't remember the name off the top of my head. You should probably avoid using the drive too much in the meantime.

---

### Post by oldfred on 2012-02-01
Testdisk may be able to restore partition if that is the issue.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

