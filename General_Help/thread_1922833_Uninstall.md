---
title: "Uninstall"
date: 2012-02-09
forum: General Help
---

### Post by marcelbrabson on 2012-02-09
I downloaded Ubuntu 12.04 and installed it in a HP Pavilion DV7-6166nr. I was going to have it as a dual boot system. The problem is now I can't boot Windows 7 64 Bit. Can anyone tell me how I can uninstall Ubuntu. I'm just going to get a separate drive for it. Thanks

---

### Post by Mark Phelps on 2012-02-09
If you "installed" it from inside Win7 (using Wubi) the only "clean" way to uninstall it is from inside Win7 like any other application.

But, if you can't boot Win7, you can do the following (to remove the bulk of Ubuntu):
1) Boot from an Ubuntu CD
2) Choose the Try Ubuntu option
3) Go to the Home icon on the top left and look through the list of partitions to find your Windows partition.  When you find it, double-click it.  That should mount your Windows partition read/write.
4) When Nautilus opens, browse through your Windows partition, looking for a root.disk file.  When you find it, Delete it.
5) Close the Nautilus window
6) Right-click on the drive icon in the launchbar (on the left) for the Windows partition and select Safely Remove.

What's left now in Win7 is the boot loader entry for Ubuntu -- which you will have to clean up from inside Win7.

---

### Post by marcelbrabson on 2012-02-09
> **Mark Phelps said:**
> If you "installed" it from inside Win7 (using Wubi) the only "clean" way to uninstall it is from inside Win7 like any other application.

But, if you can't boot Win7, you can do the following (to remove the bulk of Ubuntu):
1) Boot from an Ubuntu CD
2) Choose the Try Ubuntu option
3) Go to the Home icon on the top left and look through the list of partitions to find your Windows partition.  When you find it, double-click it.  That should mount your Windows partition read/write.
4) When Nautilus opens, browse through your Windows partition, looking for a root.disk file.  When you find it, Delete it.
5) Close the Nautilus window
6) Right-click on the drive icon in the launchbar (on the left) for the Windows partition and select Safely Remove.

What's left now in Win7 is the boot loader entry for Ubuntu -- which you will have to clean up from inside Win7.

Can't find root.disk file anywhere

---

### Post by Mark Phelps on 2012-02-10
Would have saved time if you had told us HOW you installed it.  We're not mind readers here ...

Go to the link below and download and burn the Boot-Repair ISO to CD:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

Boot from that CD and run Boot-Repair.  That should restore your Win7 boot capability.

Once you can boot back into Win7, open the Disk Management utility and remove the partition(s) you created for Ubuntu.

---

