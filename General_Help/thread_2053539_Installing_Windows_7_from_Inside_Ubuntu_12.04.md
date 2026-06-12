---
title: "Installing Windows 7 from Inside Ubuntu 12.04"
date: 2012-09-05
forum: General Help
---

### Post by binsky734 on 2012-09-05
To start off, I do not want to install a virtual machine, and I do not want to run Windows programs in Ubuntu.

I recently scrounged an 80GB IDE drive out of an old computer. Since this size is nearly perfect for my music collection, and since there isn't a good way to manage my iPhone using Ubuntu, I decided to load Windows 7 on this hard drive and use it exclusively for iTunes. I formatted the hard drive, installed Windows 7 Enterprise, then realized that I had lost my product key. No problem, I had a copy of 7 Home Edition, so I popped it in, formatted the drive again, and attempted to install. This time I was told that Windows could not create a system partition (no clue why).

What I want to know is if there is any way to run the Windows 7 installation from inside of Ubuntu (which is, of course, on another hard drive).

Thank You

---

### Post by VishnuNJ on 2012-09-05
To start off, Use BANSHEE media player to use with iDevices.. 

Windows problem.. Create New MBR to fix problem "Windows could not create a system partition"

**Installing Windows 7 from Inside Ubuntu 12.04: NO IDEA.. **

---

### Post by oldfred on 2012-09-05
The Windows system partition needs to be a primary NTFS formated partition with the boot flag. If it does not have boot flag it may not install to a NTFS partition.  Is the install seeing the 80GB drive and not your LInux drive?

---

### Post by Mark Phelps on 2012-09-05
> **binsky734 said:**
> ... 

What I want to know is if there is any way to run the Windows 7 installation from inside of Ubuntu (which is, of course, on another hard drive).

Thank You

As far as I know, except for using Virtual Box, there is no way to install Windows from inside Ubuntu.

---

### Post by Mario Fish on 2013-06-02
Try following [_[COLOR=#0000cd]THIS METHOD[/COLOR]_](http://forums.bizhat.com/linux-freebsd-opensource/59013-how-install-windows-7-ubuntu-without-burnning-disc.html) which worked last time I gave it a hurl, though that would have been in 10.04 so chances are someone will explain how it won't work under later Ubuntu versions.

---

