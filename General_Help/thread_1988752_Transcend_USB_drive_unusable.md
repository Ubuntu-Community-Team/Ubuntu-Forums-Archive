---
title: "Transcend USB drive unusable"
date: 2012-05-28
forum: General Help
---

### Post by Superpelican12 on 2012-05-28
I have a 16 GB Transcend Ultraspeed USB drive. Which I can't use anymore. It's LED is on. And it shows up in Nautilus and Disk Utility. However Disk Utility says it is not mounted. And when I try to mount it with Disk Utility it says "/dev/sdb1 is busy". I also can't format or delete a partition, it always says it is busy. How can an unmounted USB drive be busy? And how can a unmounted USB drive even show up in Nautilus? I also can't safely remove it (because it seems to be busy). So I have to pull out the USB drive without safely removing it.

What' s wrong? This USB drive wasn't cheap and I still have some files on it (don't remember if they are really important, but if it is possible to keep them, that would be nice).

EDIT: Have tried the USB drive on a Windows 7 system. On Windows 7 everything is normal and I can use the USB drive. Also I have seen on Win7 that the drive doesn't contain important files, they may be deleted. Have also tried to connect the USB drive to another USB port, but that didn't seem to help either. Now in Gnome Fallback mode (which is another problem, see my thread in the DE section) when I click on places and then on the name of my USB drive it shows an error dialog "Unable to Mount <name of my USB drive>", "This operation is already pending".

---

### Post by fantab on 2012-05-28
Is there any Transcend autorun/exe in the said drive? or any other Transcend software?  If there is , then that can cause problems. You can Format the drive in Windows and try again.

---

### Post by kurt18947 on 2012-05-28
Is Transcend still 'adding value' by including U3?  That seemed to cause me some problems with a Transcend USB drive a few years ago.  You can get a utility to remove U3 but I believe removing U3 will also remove any data present.

---

### Post by Superpelican12 on 2012-05-29
Yes the Transcend  Usb drive does come with software.
When you plug in the drive a virtual CD drive appears with
Transcend Secure.... software. However I have found out that
all my USB storage devices have the problem,  Kingston and TakeMS
USB drives (which are formatted several times, I use them dor Linux Live
Startupdisks) and my Sandisk SD card ( which I have also formatted once)
also have the problem. 

So it can't be anything Transcend-specific.

---

### Post by HermanAB on 2012-05-29
Use the mount command to see what is mounted.  Your troubled disks are probably already mounted, but messed up.  Unmount the troubled disks, possibly by using the -l parameter (lazy unmount), then mount them again.

---

