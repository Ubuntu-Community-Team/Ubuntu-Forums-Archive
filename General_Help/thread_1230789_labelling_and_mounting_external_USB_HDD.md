---
title: "labelling and mounting external USB HDD"
date: 2009-08-03
forum: General Help
---

### Post by trv75 on 2009-08-03
Hi -
I have an external USB HDD I want to reformat in EXT3, and relabel (and have it automount when plugged in.

I was able to format the drive, then followed these directions: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

But now, the label never seemed to "stick". Also, now after try to dismount and remount the drive, I cannot seem to get it to mount at all.

Are there some concise steps I could take to solve this issue?  I don't need it formatted in vfat or anything, as this is just going to be a backup drive for linux.

Thanks.

---

### Post by Gadgetech on 2009-08-03
I did a post on my blog about [adding a new hard drive in Ubuntu]("http://tuxtweaks.com/2008/11/how-to-add-a-new-hard-drive-in-ubuntu/"). The procedure should work for a USB drive as well. Since you have already formatted it, you may be able to start with the permissions part - create and delete files for the **plugdev** group.

---

### Post by scouser73 on 2009-08-04
Visit [[COLOR="Red"]**Here**[/COLOR]]("http://it.toolbox.com/blogs/php-bsd-me/formatting-and-mounting-an-external-hard-drive-with-ubuntu-linux-606lts-28211") for the tutorial about mounting a drive and then visit [[COLOR="Red"]**Here**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive") for renaming a hard drive.

---

