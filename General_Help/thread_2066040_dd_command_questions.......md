---
title: "dd command questions......"
date: 2012-10-03
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-10-03
I have a small ssd, with the complete Xubuntu install on the SSD. It's FAST, I love it!!!

I spent considerable time setting up my system so it has all the utility programs I like as well as other customizations.

Now, I want to back up the small SSD, which is 32 GB. I have a 330 GB harddrive with plenty of partitions for keeping my digital terrain database and music files etc.

It seems the best command to use is the dd command, it's free, comes built in and it's easy to use.

I assume that the dd command will allow me to specify which partition (on the HDD) I want to send the data to.

Once my SSD has been cloned on the HDD....I think I can use gparted to reduce the size of the HDD partition so that it will be smaller than 32 GB. 

**If I use gparted to make the HDD partition smaller than 32 GB SSD, can I then clone (using dd) the HDD partition back onto the SSD if needed?????**

Also, since I have my entire system on the SSD, is it really necessary for me to have the 8GB swap partition at all??? 

I'm having a blast with linux, thanks to all who contribute to this forum and/or support linux in some way.

Regards,

Art

---

### Post by Cheesemill on 2012-10-03
Instead of dd I would recommend using [Clonezilla]("http://clonezilla.org/").

Just boot from the Clonezilla Live CD, select your SSD as the source and a folder on your HD as the target. Clonezilla only copies the parts of the filesystem that are actually being used and compresses them, so your image will end up smaller than the space you are using on your SSD.

---

### Post by goodbye-windows(tm) on 2012-10-03
> **Cheesemill said:**
> Just boot from the Clonezilla Live CD, select your SSD as the source and a folder on your HD as the target. Clonezilla only copies the parts of the filesystem that are actually being used and compresses them, so your image will end up smaller than the space you are using on your SSD.

I understand compression and how it makes the resulting file smaller. 

But, how can clonezilla only copy the files that are in use???? What exactly does that mean? 

I played around with clonezilla before, but they make you go through this long list of questions and that makes me uncomfortable as I don't understand the questions completely.

Art

---

### Post by Cheesemill on 2012-10-03
> **goodbye-windows(tm) said:**
> But, how can clonezilla only copy the files that are in use???? What exactly does that mean?
Not the files that are in use, the parts of the filesystem that are being used.
Basically it means it doesn't copy unused free space like the dd command would.
> I played around with clonezilla before, but they make you go through  this long list of questions and that makes me uncomfortable as I don't  understand the questions completely.
It's actually much easier than it seems, most of the questions you can just hit Enter to select the default options.

Instructions and screenshots for exactly what you are trying to do can be found here:
[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

---

