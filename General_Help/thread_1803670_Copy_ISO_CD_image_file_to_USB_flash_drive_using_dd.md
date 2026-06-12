---
title: "Copy ISO CD image file to USB flash drive using dd?"
date: 2011-07-13
forum: General Help
---

### Post by Monocerotis on 2011-07-13
Hello everyone!

I am pretty much a noob when it comes to Linux. But I desperately need to do exactly what the title of this thread says.

I have this ISO file which is a bootable CD image. But instead of booting off of a CD, I want to boot from a USB flash drive. I understand that I can't simply just burn it with ImgBurn or whatever, and then just drag and drop the files and folder to a USB flash drive. Because hidden files, bootloader, etc. would not be visible and not copied. I know I'm in for some special software in order to copy every single byte from that ISO image to my USB flash drive.

I did try extracting the ISO with PeaZip (7-zip based) under Windows Vista, but that didn't work out very well. It resulted in a few files and folders, totaling in at about 2 KB, while the source ISO file is actually some 50 MB. WinRAR, on the other hand, would simply just create an empty folder where to put the files (no files created/extracted), flash before my eyes and call it a day ("complete").

I have learned from other posters on other forums that there is this Unilx program/command called DD. How can I use DD to accomplish this task?

Thank you!

---

### Post by foutes on 2011-07-13
Change sd* to sdb or sdc,whatever your thumb drive is labelled

Also this will delete any data already on the thumb drive. 



```
sudo dd if=/path/to/downloaded.img of=/dev/sd*
```

---

### Post by C.S.Cameron on 2011-07-13
A lot depends on what you want to boot.
Many Linux distro iso images can be booted from USB flash drive using the MultiBootUSB script:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
For XP you need something like:
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)
For Windows 7 you can format the stick NTFS and set the boot flag, (gparted), then extract the iso image to the flash drive, (or copy the Files from the DVD).

---

