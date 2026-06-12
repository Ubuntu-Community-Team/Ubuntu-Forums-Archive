---
title: "Questions about cloning my computer's HD"
date: 2011-01-18
forum: General Help
---

### Post by JEBB on 2011-01-18
Dell Mini 9, 2GB RAM, 32GB SSD, Ubuntu 10.04 UNR
My DM9 has a 32GB SSD of which only 4.3GB is used.  I would like to know if, and how, I can make a bootable clone of the HD as a backup (an exact copy of the files and data on that drive) onto a 8GB flash drive.  I suspect I would use more than just the command:  "dd if=/dev/sda of=/dev/sdb", correct?  Thanks

---

### Post by baddnady23 on 2011-01-18
You can use many programs... Popular ones that you could look at would include dd, clonezilla, gddrescue or partimage.  The thing with dd is that you need to be copying the source drive to one that is of equal or greater size if I am not mistaken.

I have been looking into cloning alot lately for the purpose of backups and I have found quite a few great resources, here is a great start:

[https://help.ubuntu.com/community/DriveImaging]("https://help.ubuntu.com/community/DriveImaging")
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery") -- Look under gddrescue on this one.

---

