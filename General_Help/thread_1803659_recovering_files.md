---
title: "recovering files"
date: 2011-07-13
forum: General Help
---

### Post by zero2491 on 2011-07-13
My parents windows hdd crashed a few months ago. So i installed ubuntu 10.04 and recovered all their files. I just recently gave them a new hdd and went to install win on it but it ended up installing on the ubuntu hdd. So i took that hdd out and installed on the other hdd. My problem now is that they had ubuntu for a few months and i am trying to recover the files off the ubuntu hdd but whenever i boot to that hdd it tries to load windows. I ran a live cd of ubuntu but whenever i try to copy the files to a external it says i do not have permission to move the files. I deleted the windows partition but the boot loader is still looking for windows.

Is there away in a live cd to get past the permissions so i can recover their documents.

---

### Post by nothingspecial on 2011-07-13
> **zero2491 said:**
> 

Is there away in a live cd to get past the permissions so i can recover their documents.

Yes.

```
gksudo nautilus
```

---

### Post by Mark Phelps on 2011-07-13
> **zero2491 said:**
> My parents windows hdd crashed a few months ago. So i installed ubuntu 10.04 and recovered all their files. 
Was this a dual-boot in which you had Windows and Ubuntu on the same physical drive?  Or, did you connect the former Windows drive to the PC and recover their files using Nautilus in Ubuntu?

> I just recently gave them a new hdd and went to install win on it but it ended up installing on the ubuntu hdd.
So, you had two drives connected and installed to the wrong one?  Did one drive still contain Windows, and was it bootable for Windows?

>  So i took that hdd out 
The one you mistakenly installed Ubuntu to? Or the one with Windows still on it?
> and installed on the other hdd. 
Sorry, confused regarding which drive is which -- now.

> My problem now is that they had ubuntu for a few months and i am trying to recover the files off the ubuntu hdd but whenever i boot to that hdd it tries to load windows.
It would do that if that drive booted Windows and the "other" drive booted Ubuntu.
>  I ran a live cd of ubuntu but whenever i try to copy the files to a external it says i do not have permission to move the files. 
Answered in the previous post.

> I deleted the windows partition but the boot loader is still looking for windows.
The Boot Loader or the MBR?  The boot loader is contained INSIDE a Windows partition, so if you deleted THAT partition, there is no Windows Boot Loader.

However, if this was a Windows 7 PC, and it came preloaded with Win7, the boot loader was installed to a separate "boot" partition, not to the Win7 OS partition.  So, removing the Win7 OS partition still leaves the boot loader in place -- which will fail because it be unable to actually launch Windows 7.

> Is there away in a live cd to get past the permissions so i can recover their documents.
Answered in previous post.

---

