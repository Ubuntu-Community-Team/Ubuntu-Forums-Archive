---
title: "copy to usb stick stalls after some seconds"
date: 2011-08-12
forum: General Help
---

### Post by ritti on 2011-08-12
Hi, I hope to post my issue in the right Thread :)

I just installed Ubuntu 11.04 on my workstation (MB Asus P6X58D Premium) and cannot copy large files (350 MB) to USB Sticks. If i copy one file the copy dialog hangs at ~99% and if I Try to copy 2 or more files it hangs after 99% of the first file but if the files are smaller (3-5 MB) it copies about 5 files but not more.
(Its the same if i try to create a USB Startup disk or if I copy from the terminal)
I tried different filesystems (ext3 fat32 ntfs) but its always the same bug
I tried 2 different Sticks with the same result but both sticks work on a 10.10 box or with win7. 
/var/log/syslog says:
kernel: [  785.585933] usb 2-6: reset high speed USB device using ehci_hcd and address 8

I read about a similar bug in natty beta 1-2 but it should have been resolved with release i think.

Edit: I just tried to copy some files to a USB HDD and it Stalls after about 10% of the second file (432 MB of 700).

Ritti

---

### Post by ritti on 2011-08-13
lol you won't believe it...
I restartet into Windows again to see if it's really still working now.
I noticed that my mouse and keyboard always restarted (I couldnt notice that in ubuntu because the usb driver were resetted instantly) So i plugged out my usb cable from my pc to the monitor usb hub and so I was able to copy to usb devices again. By the way, this solved my suspend resume bug too XD

---

