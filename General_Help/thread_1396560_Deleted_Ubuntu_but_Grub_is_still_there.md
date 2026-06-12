---
title: "Deleted Ubuntu but Grub is still there"
date: 2010-02-02
forum: General Help
---

### Post by tesseract4d on 2010-02-02
Hello,

I wanted to redo my whole lap - which had windows 7 and ubuntu dual booted - in the sense uninstall and install everything again all over.

So I first erased the Ubuntu partitions using Windows 7 - went to disk management and deleted the volumes. Little did I think about grub being my boot loader.

When I restarted the machine I got the following error message:

"
GRUB Loading stage1.5.

Grub Loading, please wait...
Error 17
"

I am yet to receive my new copy of Windows 7 - and until then I can't get anything done. Tried using the windows 7 recovery disc, and the Ubuntu live CD but with no success.

Any help on what I can do?

---

### Post by NightwishFan on 2010-02-02
Use a supergrubdisk to repair Windows MBR. Windows Recover Disk should be able to do this as well, though I do not know how. On SuperGrubDisk, the option is called "Fix Boot Of Windows"
[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso)

If you want Ubuntu Installed, you can just repair grub using Ubuntu install CD.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by aseibert on 2010-02-02
You actually should be able to use the Windows 7 disk.  Boot it up, and go to the recovery console, and select "fix boot errors."  That should overwrite the MBR.  Or, you can use the command prompt in the recovery console and do the following:

Bootsect is located inside the boot folder so change your directory to boot. Now run "bootsect /nt60 C:\" if you had Win 7 initially installed in the C partition. Alternatively, you can run "bootsect /nt60 SYS" or "bootsect /nt60 ALL" to repair the system partition or all partitions. Eject the DVD, and restart computer. Your computer should now boot Win 7 again.

---

### Post by audiomick on 2010-02-02
Hi.
You can restore the Windows mbr using the Ubuntu live CD.
go here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
and follow the instructions under point 16 in the first post.

---

### Post by Grenage on 2010-02-02
If you can get to a windows recovery console, you can install a windows bootloader.  Failing that, you could reinstall GRUB using a livecd - you can use GRUB to boot windows.

Edit: The previous poster has a much more elegant solution.

---

### Post by bilalakhtar on 2010-02-02
Follow these steps:-
1) Insert the Windows 7 cd in the drive
2) Restart the computer
3) Boot from the CD
4) When a blue screen comes, select the option to "repair a windows install" or similar.
5) A dialog box will come. Select the last option, saying "Access the command prompt"
6) Once the prompt opens, type ```
bootrec /fixmbr
``` to restore the Windows 7 bootloader.
7) Restart the computer.

---

### Post by bilalakhtar on 2010-02-02
Follow these steps:-
1) Insert the Windows 7 cd in the drive
2) Restart the computer
3) Boot from the CD
4) When a blue screen comes, select the option to "repair a windows install" or similar.
5) A dialog box will come. Select the last option, saying "Access the command prompt"
6) Once the prompt opens, type ```
bootrec /fixmbr
``` to restore the Windows 7 bootloader.
7) Restart the computer.

---

### Post by tesseract4d on 2010-02-02
Sorted it out. 

Took bilakhtar's advice first up because it was the simplest to implement=> and it worked.

Thanks a lot guys - esp for responding very soon.

---

