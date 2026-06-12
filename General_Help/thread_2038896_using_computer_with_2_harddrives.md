---
title: "using computer with 2 harddrives"
date: 2012-08-07
forum: General Help
---

### Post by Felixmpena01 on 2012-08-07
Hello everyone, i have a windows computer with 2 harddrives one for the OS and the second one for the ubuntu server, how can i access the ubuntu server while my os side it's running, thank you , any help will be appreciated.

---

### Post by drmrgd on 2012-08-07
Without running one of the in a virtual machine (like one of the VMware products, Virtual Box, Windows Virtual PC, etc.) I don't think you can simultaneously run two OSes at the same time, even if they're on different hard drives.  Is virtualization an option for you?

---

### Post by Felixmpena01 on 2012-08-07
> **drmrgd said:**
> Without running one of the in a virtual machine (like one of the VMware products, Virtual Box, Windows Virtual PC, etc.) I don't think you can simultaneously run two OSes at the same time, even if they're on different hard drives.  Is virtualization an option for you?

ok i see , now the thing is also that when i put ubunto on the second harddrive and then i boot my computer i dont see the harddrive listed anymore on my list, is there a way to acces the hardrive using the Windows OS or it wont recognize it , beccause of the ubunto Server on it?

---

### Post by drmrgd on 2012-08-07
Windows doesn't know how to read linux formatted hard drives (like ext3, ext4, etc).  So, when you're in Windows, you won't be able to see that drive.  The converse is not true, though, and linux can read from NTFS (Windows) formatted hard drives.  

What you'll need to do if you want to dual boot the two operating systems is set up a boot loader (typically Grub) to load both OSes at the start.  There are a few experts on setting that up on this forum!  If you'd like to do that as opposed to setting up a virtual machine, it might be helpful to get a little more info about how your system is setup.  I'd recommend booting into Ubuntu and downloading the most recent version of Bootinfo Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then paste the results using the "Code" tags (the little hash sign) so that we can see how you've partitioned things and where you have your boot flag set.  After that it's a simple matter of setting grub up to allow to you choose which OS you want to boot to.

---

