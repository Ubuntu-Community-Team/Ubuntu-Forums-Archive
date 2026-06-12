---
title: "usb drive used for bootable now does not work"
date: 2010-03-09
forum: General Help
---

### Post by triplemaya on 2010-03-09
I used my large backup usb drive to install remix on a netbook, which went fine. during the setup I was given the option to keep my other files on this drive which I accepted. After the install I went on using the drive as my backup, but it behaved strangely, so I have been trying to clean everything off the drive. I have deleted the partition and reinstalled it, but I still have problems. All the time the usb drive is installed a new nautilus window appears with that directory every minute. When I try to back up to the drive, most of the directories I want to write to can not be written because I don't have permissions to write to this drive.
Please could someone tell me how to completely wipe this drive so I can use it as I used to do.
One more thing, when I wanted to change the label on the drive, I followed instructions to use gparted, which says I have to unmount the drive and then change the label. As soon as I unmount the drive it is not visible in gparted.

---

### Post by triplemaya on 2010-03-09
Solved
Using a windows machine simply download a free low level formatting tool, after the low level format a quick format to fat32 takes about 30 seconds, and you can set the label at the dos prompt with label :[current label] [name you want label to be]
Windows definitely seems to be king here!

---

