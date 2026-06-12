---
title: "Disk Partitions Not Showing"
date: 2012-08-17
forum: General Help
---

### Post by Raptured00 on 2012-08-17
So, I am running Ubuntu 12.04 (precise) on a partition of my Windows PC. I am trying to access a third drive partition that I have, but it is no longer showing up in the file manager. I was able to access it two days ago, but haven't since I did a recent reboot. I don't recall making any changes to the system.

I'm not sure if it's a permissions issue or something else. I am logged in as the administrator and have tried using the command line to get to the path I know the drive existed before ( /media/Backup Volume), but the media folder is now empty.

I have also tried to mount the drive, but I don't think I'm doing it correctly since it's not really a device.

I searched the forums for anything on point, but couldn't find anything. Any thoughts?

Thanks for any help that may come my way.

---

### Post by lindsay7 on 2012-08-17
Type fdisk -l in the terminal and post the results here. That is the lower case letter L.

---

### Post by nothingspecial on 2012-08-18
*Thread moved to **General Help**.*

---

### Post by Raptured00 on 2012-08-31
> **lindsay7 said:**
> Type fdisk -l in the terminal and post the results here. That is the lower case letter L.

Actually, I figured it out. It was probably just my not being used to Ubuntu yet. When I was looking at the file manager before it listed only "Home" and "File System".  When I executed the fdisk command I saw that my partition was showing as "hidden". So I went and tried to see if there was an option to show all files or something like that. The options menu showed an option for "Computer". When I selected it, it showed all of the items that had been listed in the terminal with fdisk. And, of course, there was my hidden drive.

---

