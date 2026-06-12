---
title: "Random Win7 Freezes after Ubuntu 1.0.10 Install."
date: 2010-10-16
forum: General Help
---

### Post by souldevour on 2010-10-16
Yo All,

I currently have Windows 7 Ultimate 64 running on my Asus laptop. I decided to install Ubuntu 10.10 along side Windows, as I will need it for work. It was installed via side-by-side and re-sized the partition

The installation of Ubuntu was flawless and works great, but now when I boot to Windows, its will randomly freeze, sometimes in 1 minute, sometimes within 10 minutes.

The only way I can solve this issue, is to either perform a disk scan from windows or restore the MBR.

The disk scan works, and Windows run fine, although If I boot Ubuntu again, run that for awhile, then boot windows again the problem returns.

Restoring the MBR works as well, though without a dualboot, its useless :P

I have also tried EasyBCD and replaced GRUB with Windows boot manager, though same problems.

Any advice on this, or perhaps a known fix for this issue?

Cheers

---

### Post by TeoBigusGeekus on 2010-10-16
Have you defragmented the windows partition before installing ubuntu?

---

### Post by efflandt on 2010-10-16
For Vista or Win7 it is generally recommended to first shrink your Windows partition from Windows Computer Management itself.  Then from Linux create whatever partition(s) you want for that.  Although, I have never had any trouble resizing ntfs partitions from Linux, other than having to disable virtual memory in WinXP before doing that if a system partition (otherwise amount of shrinkage may be limited), then re-enabling virtual memory afterwards.

It you set Windows to check its C: drive and fix errors automatically (which requires reboot), does it find and fix any errors when it reboots?  Or try checking both boxes in the disk check window to do a more complete scan of your drive for bad sectors.

---

