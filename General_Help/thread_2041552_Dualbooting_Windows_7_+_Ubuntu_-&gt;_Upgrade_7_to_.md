---
title: "Dualbooting Windows 7 + Ubuntu -&gt; Upgrade 7 to 8"
date: 2012-08-12
forum: General Help
---

### Post by andeh19 on 2012-08-12
Hi,

Right now I am dualbooting Windows 7 with Ubuntu 12.04 using GRUB.  I am planning on upgrading Windows 7 to Windows 8 RTM, I was wondering if this will cause any problems with GRUB? If so, how can I do this properly?

Thanks!

---

### Post by marlow59 on 2012-08-12
This thread is open on the wrong section please move it to Update&Installation category; Anyway to answer your question:
 Not only will it cause a problem with Grub, it will literally remove it =). For a step by step guide on how to install a new Windows partition without removing Grub see this : not only will it cause a problem with Grub, it will literally remove it =). For a step by step guide on how to install a new Windows partition without removing Grub see this :[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")

---

### Post by oldfred on 2012-08-13
Marlow's link will get you there. 

Two more links to instructions.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

But be aware:
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

