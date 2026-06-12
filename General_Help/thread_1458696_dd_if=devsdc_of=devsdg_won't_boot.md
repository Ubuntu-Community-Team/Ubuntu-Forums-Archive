---
title: "dd if=/dev/sdc of=/dev/sdg won't boot"
date: 2010-04-20
forum: General Help
---

### Post by Netdes on 2010-04-20
Hi, I am try to clone a ubuntu system on a 8G CF. 
I use another ubuntu system and insert the target CF into a usb multi-card reader, then "df -h -T" to found out the drive (/dev/sdc1). 
Then insert another CF into a second usb multi-card reader, "df -h -T" to found out (/dev/sdg1).
Both CF are Kingston 8GB (but different speed grade).
Then I "sudo su" then "dd if=/dev/sdc of=/dev/sdg"
I came back without error.
Then I ejected both USB. Put the copied CF into the old machine but it did not boot up.
It did not boot up, "GRUB ..  Error 16"   , sound like file system issue.

I repeated a few time same result.
Tried   "dd if=/dev/sdc of=/image.img" on source CF   "df if=/image.img of=/dev/sdc"  on to a different CF.

Any suggestion.
  
Ed

---

### Post by Seq on 2010-04-20
Silly question, but I assume your original card boots properly?

---

### Post by Netdes on 2010-04-20
Yes, the original CF still boot after the copying.
Look at it carefully I found out the copying ran out of space.
Even though both CF is of the same vendor and same size. But look like the original one is slightly larger.    

Is there a way to "clone" a bootable CF from a larger size to a smaller one? 
Manually partition the disk?, copy all files, somehow set up the boot?

Regards, Ed

---

