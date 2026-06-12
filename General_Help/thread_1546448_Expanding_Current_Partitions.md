---
title: "Expanding Current Partitions"
date: 2010-08-05
forum: General Help
---

### Post by tmos22 on 2010-08-05
I installed Ubuntu 10.4 just thinking that I would need 20GB for it. But I find myself using it more and more often. How do I expand the current partition that it is on. 

I am dual booting it with Windows 7. But now I just want a couple of 100GB for Windows 7 Gaming and the rest of the memory for Ubuntu.

---

### Post by dv3500ea on 2010-08-05
Boot from the live CD and use the partition manager (gparted).

You will need to shrink the Windows partition and move/expand the ubuntu partition.

Make sure you back up important files first.

---

### Post by tmos22 on 2010-08-05
Ok thanks, I'll try it now

---

### Post by ajgreeny on 2010-08-05
Wait!  Wait!  Wait!

You should really only shrink the win7 partition with win7's own disk management utility, not gparted.  You may be lucky, but if I am too late, you may find that win7 objects when you next try to boot to it.  I hope I am wrong, but at least you will not be totally surprised if you are unlucky.

Unfortunately I have no idea how you deal with such a windows problem, should it arise.

Best of luck.

---

### Post by What Rights on 2010-08-05
> **ajgreeny said:**
> Wait!  Wait!  Wait!

You should really only shrink the win7 partition with win7's own disk management utility, not gparted.  You may be lucky, but if I am too late, you may find that win7 objects when you next try to boot to it.  I hope I am wrong, but at least you will not be totally surprised if you are unlucky.

Unfortunately I have no idea how you deal with such a windows problem, should it arise.

Best of luck.

ajgreeny is right, if you use gparted you will have to run a chkdsk for Windows 7. Your best bet is to use Windows.

Start>Computer>(right click)Manage>Disk Management> etc.

---

