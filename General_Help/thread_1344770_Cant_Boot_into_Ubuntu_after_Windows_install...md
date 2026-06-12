---
title: "Cant Boot into Ubuntu after Windows install.."
date: 2009-12-03
forum: General Help
---

### Post by azteka22 on 2009-12-03
Hello everybody,

I formated my hdd and made 3 partitions. 1 (ntfs) for windows, 1 for swap and the other one (ext) for ubuntu 9.10. 

I first installed windows 7 configured it, then i installed ubuntu 9.10 and installed grub as my default bootloader. and everything was working perfect, i could dual boot into windows 7 and ubuntu 9.10 on my desktop. btw both of these OS are 32-bit.

Later i installed a second hdd on my desktop computer and i formatted that hdd as NTFS b/c i wanted to install windows server 2008 on it. i installed windows server 2008 on that hdd and now it deleted the grub bootloader and i can now only boot into windows 7 or windows server 2008..

i read some posts about how to get grub loader back but i have not yet succeeded. I tried the super grub disk and tried to fix the linux grub bootloader but it says it cannot find the /boot/grub/stage1 file. it says file not found.

then i tried the livecd of ubuntu 9.10 and i mounted my partition and everything is there, all my files are there and everything so i kno i didnt delete that partition. i tried to install grub through the livecd, i did sudo grub, find /boot/grub/stage1 and it still says file not found. 
then i tried to manually find it, i went onto my partition and opened the boot folder then the grub folder and the file is not there.. 

How can i get grub back into my system so i can boot into ubuntu again? 

anybody have any ideas? thx in advance

---

### Post by gspat on 2009-12-03
Try this link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope it helps!

---

### Post by azteka22 on 2009-12-03
Thank u! it worked perfectly !

---

