---
title: "GRUB Hard Drive Scan?"
date: 2009-12-28
forum: General Help
---

### Post by Dr Belka on 2009-12-28
So I had ubuntu 9.10 installed on my computer.  After a little while of using that, I decided it was a little to slow for my small amount of RAM so I installed Crunchbang Linux.  When Crunchbang Linux installed GRUB, it "scanned the hard drive" and found my old ubuntu installation, and added entries in menu.lst accordingly.  I decided to install Debian Lenny to play around with, so I deleted my ubuntu partition and installed Debian in the leftover space, but I did not allow the debian installation to install a boot loader.  I manually added the entry to my menu.lst file for debian to boot.  I did notice that when I ran "update-grub" when I still had my ubuntu and crunchbang installations, grub would find new kernels in  both the #! and the Ubuntu partitons.  While I can currently get Debian to boot just fine, I was wonder why "update-grub" does not find any new kernels on my debian installation, as it would if crunchbang was installed after debian.

Does my question make any sense to you guys?

Thanks

---

