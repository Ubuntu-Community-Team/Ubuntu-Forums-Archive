---
title: "dual boot windows 7 and ubuntu"
date: 2011-06-20
forum: General Help
---

### Post by tramposo on 2011-06-20
Hello everybody.
This is my first post, and I really need help.
I've done a lot of research online and I could not find any answers.
I've got Ubuntu 9.10 installed on my laptop (really nice one as well, i7) which has two 500Gb HDDs (on one of them).
Now I need Windows 7 for work (stupid standards), so I bought the windows 7 64 bit. :7
Whenever I try to install Windows 7 on one of them, I get this message:

"Setup was unable to create a new system partition or locate an  existing system partition. See the Setup log files for more information."

I've read that the ONLY solution is to disconnect the HDD, but I really do not want to open up my laptop.
So I tried everything, starting from pressing <F10>, and then playing with diskpart:
diskpart
diskpart>select disk 0
diskpart>clean
diskpart>create partition primary
diskpart>format fs:ntfs

Then I burned a gparted livecd, formatted the disk in ntfs, but still did not work.
I opened up bios, and set disk 0 to be the bootable one, and not the one with ubuntu, but still nothing...

Please help, as I do not want to remove Ubuntu from my laptop, and start all over...

---

### Post by tramposo on 2011-06-20
no ideas?

---

### Post by oldfred on 2011-06-20
Windows system partition needs to be a NTFS formated primary partition with the boot flag. If the drive is blank, windows will also install to that and usually installs to two primary partitions. One 100MB boot/recovery & the main install. If you have a primary NTFS partition it will see that if it has the boot flag (active partition in windows) and install all of the system in the one partition.

This discusses Vista & dual boot, but 7 is the same except for the new 100MB boot partition.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Are you installing windows to one drive with Ubuntu on the other. You need to make sure your grub boot loader is installed to the Ubuntu drive. Then set BIOS to boot the other drive so windows sees it as the boot drive and it should install its boot loader to the windows drive. Once you confirm it boots ok, then in BIOS change back to the Ubuntu drive, boot Ubuntu and run this to find windows (if grub2). If grub legacy it may not find windows.

sudo update-grub

I thought the i7's required the newest kernels in 11.04?

---

