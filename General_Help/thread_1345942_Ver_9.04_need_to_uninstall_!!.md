---
title: "Ver 9.04 need to uninstall !!"
date: 2009-12-04
forum: General Help
---

### Post by loybanks on 2009-12-04
I've recently installed Ubuntu Ver 9.04 next to Windows Home Edition. The install was clean. But there isn't enough space on the drive for both systems.

So I want to completely uninstall Ubuntu from that drive.

Then I'm going to install another hard drive to handle Ubuntu.

So how do I go about completely uninstalling Ubunto from the drive?

Thanks

---

### Post by Snow986 on 2009-12-04
Boot into Windows Recovery Console using your XP install CD and run fixmbr to clear the master boot record.

Once you do this and boot straight into Windows, right click My Computer, select Manage, go to Disk Management, and delete the Linux partitions. Then use those partititions for whatever you want or merge them back into your Windows partition.

---

### Post by loybanks on 2009-12-04
Thanks so much. That concept seems logical. But I need another related answer, if you might know the answer that is.

I've tried booting into the Recovery Console. I haven't done that in years. :) My problem is, it 's asking me for a password in order to enter it. However, I don't have any passwords of any kind installed on the system. 

So what password must I use to enter? I'm between a rock and a hard place. Thanks so much for your help.

---

### Post by RJ12 on 2009-12-04
try just pressing enter at that prompt

its the pass of the Admin account (Not yours but the actual one that has ALL privileges in Windows)

---

