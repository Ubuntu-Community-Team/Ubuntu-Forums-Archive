---
title: "CHKDSK on LINUX"
date: 2011-09-09
forum: General Help
---

### Post by mahnerak on 2011-09-09
Hi
How can I check disk (ntfs) on Ubuntu(LiveCD) with tool that does same as CHKDSK in Windows?

---

### Post by TeoBigusGeekus on 2011-09-09
Unfortunately you can't.
Linux has no tool for checking (and attempting to fix) errors on ntfs disks.

---

### Post by SeijiSensei on 2011-09-09
Well, that's not entirely true.  The [ntfstools]("http://packages.ubuntu.com/natty/ntfsprogs") package includes ntfsfix which is described as able to "Fix common filesystem errors and force Windows to check NTFS."  (It marks the drive as needing a chkdsk upon reboot.) 

That said I hardly ever touch NTFS filesystems using anything other than Windows utilities.  I have successfully used ntfsresize to shrink a Windows partition before installing Linux.  That also requires a chkdsk run on the resized filesystem at reboot.

---

### Post by TeoBigusGeekus on 2011-09-09
> **SeijiSensei said:**
> Well, that's not entirely true.  The [ntfstools]("http://packages.ubuntu.com/natty/ntfsprogs") package includes ntfsfix which is described as able to "Fix common filesystem errors and force Windows to check NTFS."  (It marks the drive as needing a chkdsk upon reboot.) 
Cool, I didn't know that.

> **SeijiSensei said:**
> That said I hardly ever touch NTFS filesystems using anything other than Windows utilities.  I have successfully used ntfsresize to shrink a Windows partition before installing Linux.  That also requires a chkdsk run on the resized filesystem at reboot.

+1

---

### Post by Warren North on 2011-09-09
Interesting so if someone uses NTFS external drive they may still have to use windows for some issues. I thought I was free from windows except the other day when I connected a external drive to my ubuntu setup which I used before and and error came up say to use windows to fix. HMMMM. I guess you have to use a different drive system.
Reading this helps.Thanks again I was find able to search and find the info. Even if it is info I did not want to hear. :)

---

