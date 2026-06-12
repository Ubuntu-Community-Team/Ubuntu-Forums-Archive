---
title: "Could not find kernel image: linux on LiveUSB"
date: 2009-11-26
forum: General Help
---

### Post by DColber on 2009-11-26
Hi All,

I have had success installing a persistent Kubuntu 8.10 to a 4Gb USB drive.  Unfortunately with the programs I want (scientific software), I have run out of space (even after increasing the casper-rw file size).

So I purchased a 16Gb USB drive, with the intent of installing Kubuntu 8.10 using casper-rw and home-rw partitions as outlined here:

[html]http://ubuntuforums.org/showthread.php?t=983967[/html]And Quoting C.S.Cameron here for conveniences sake:

> This is what I did on a 4 GB flash drive:

Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changes are persistent.Everything seems right.  Partitions look OK.  Kubuntu live boot files are all present in the FAT32 partition.  Even the home-rw partition works, as on one occasion booting up my existing liveUSB, it decided the use the home-rw partition (of the separate usb drive) as the home folder.

Im relatively new to Linux, so Im not quite sure what the problem is.  Can anyone help me out?  

I have infact found this thread [html]http://ubuntuforums.org/showthread.php?t=1329570&highlight=could+-find+kernel+image[/html] which outlines the same error, but given they are booting from their hard drive, and not using the persistent liveUSB set up, I wasn't sure if it was the same problem.

Your help is much appreciated.  Please let me know if I have miseed or not been clear on anything.

---

