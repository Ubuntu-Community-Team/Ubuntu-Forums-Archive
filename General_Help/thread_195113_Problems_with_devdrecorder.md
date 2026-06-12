---
title: "Problems with devdrecorder"
date: 2006-06-12
forum: General Help
---

### Post by Hoffmann on 2006-06-12
Hello,

I am trying to read a data DVD, but I am getting the error:

> You do not have the permissions necessary to view the contents of "dvdrecorder".

How could I solve this problem?
Thanks!

---

### Post by Javahead on 2006-08-20
Hello all,

  I had the same problem and was about to post, in detail, what I experienced.  I discovered that my entry in /etc/fstab for my DVD+/-RW drive was incorrect.  I simply changed it to reflect the correct device (/dev/hdd) and it works fine now. I moved the drive and added an additional harddrive, but /etc/fstab was not automatically updated to reflect this change.  My DVD drive was previously /dev/hdc, but now /dev/hdc is a harddisk, while the DVD drive is now /dev/hdd.  What's strange is that media that was not burned by me and CD-R's would mount and be read as-is.  The harddisk was not mounted at all during this process.  


Here's what would happens:

(1) I put a burned DVD (data CD) into my drive.
(2) The CD is mounted and Nautilus opens with a browser window automatically
(3) The message "You do not have permission to access 'dvdrecorder'"

Is this a bug with automount?  I don't recall having to update /etc/fstab manually like this for device changes... at least not for a VERY long time.

Hope this helps!

---

