---
title: "External Hard Drive Permissions Issue"
date: 2010-01-01
forum: General Help
---

### Post by tomreid on 2010-01-01
Hi All,

I am moving houses very soon, so have bought a large 1TB hard drive. 

I formatted it to EXT3 using GP parted, but I have a permissions issue. 

When I go to "copy" a file to add it to the drive, when I click into the drive in Nautilus, the "paste" option is not available. When I try a drag and drop I get an error message saying "permission denied". 

When I run : [FONT=Courier New]"gksu nautilus" and run Nautilus as Root, I am able to add files to the drive no problem. 

I can't see a way to easily change the drives overall permissions to my user name and not "root". 

I would much rather use it under my user name as running Nautilus as root each time is a little convoluted. 

I partitioned the drive to EXT3 when the system was running under my account, but can only assume there was a permissions issue created when the partition was created?

Any help gratefully received. 

I'm running 9.10.

cheers
[/FONT]

---

### Post by todak on 2010-01-01
Run ```
gksudo nautilus
``` Open the **media** folder. Look for the folder with the name of the drive you want. Right-click on the folder and click on the **Permissions** tab. Change the owner and permissions as you see fit. Close Root Nautilus and read/write files to the drive as a normal user.

---

### Post by tomreid on 2010-01-02
Thanks - that seemed to work. 

I changed all the permissions to "Tom" which is my main use name I use.

One question this drive is sitting in an external enclosure and I intend to plug it into another system when i get back home. 

Assuming I use the same user name "Tom" when I set up the new system, will I be able to read and write to this disc with no restrictions on the new system?

cheers

---

### Post by todak on 2010-01-02
If the external drive is formatted as FAT32 or NTFS, etc., you can read/write files on any machine without having to set permissions each time. However, if it is formatted in one of the common permission based file systems such as etx4, ReiserFS, etc., you will need to (re)set permissions each time you attach it to a different machine.

---

### Post by tomreid on 2010-01-04
Thanks, I ended up re-formatting to NTFS to avoid these permissions issues.

cheers

---

