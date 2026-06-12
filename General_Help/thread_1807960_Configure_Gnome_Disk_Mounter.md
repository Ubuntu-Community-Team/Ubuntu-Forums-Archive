---
title: "Configure Gnome Disk Mounter"
date: 2011-07-19
forum: General Help
---

### Post by bakegoodz on 2011-07-19
Anyway I can configure Gnome's Disk Mounter, or know the mechanism it uses to mount disks (does it without elevating to root)

 I love how easy it is to use, but it doesn't support a new NTFS driver I have installed. The new driver is compatible with command line mount, but it adds a new mount type: ufsd Anyway how can I tweak Disk Mounter, or Gnome subsystem, to mount NTFS drives under this new mount type? Removing NTFS-3G makes it use the old read-only NTFS Kernel driver. After removing that kernel driver makes Disk Mounter unable to mount NTFS. The 3rd party kernel driver still works in the terminal with Mount.

Why:
I just discovered Paragon's free NTFS level kernel driver. [http://www.paragon-software.com/home/ntfs-linux-per/](http://www.paragon-software.com/home/ntfs-linux-per/) I switched from the built-in NTFS-3G driver because I transfer many GB on a drive that needs to be NTFS. Even on fast Core i5 system transfer would max at 35 MB/s take nearly all processor resources. I was shocked that my transfers increased to over 100 MB/s with Paragon's driver, and without noticeably slowing the system. Which is very nice for the tasks I do. The great difference in speed is probably because NTFS-3G isn't in the kernel, which something that won't change anytime soon. I can manually mount in the command line, but I have to do so as root and that creates file permissions headaches.

Thanks for any suggestions

---

