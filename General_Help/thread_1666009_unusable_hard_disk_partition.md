---
title: "unusable hard disk partition"
date: 2011-01-13
forum: General Help
---

### Post by mynameissagarbhatt on 2011-01-13
i've been trying to install ubuntu alongside windows 7. for that i even created a new  partition of hard disk.......now  even  after that i can't do it.....the new partiotion where i m trying to install ubuntu is declared as 'unusable'.....why is that unusable?o.0 ('cuz i can use it perfectly well in windows ) ...........all it says is 'no root file system is defined'........:confused:

---

### Post by indytim on 2011-01-13
Your new partition for installing Linux must be a compatible file type for Linux.  For installs today, the most common file systems are ext3 and ext4.   Since you said Windows has no problem seeing the partition, I'm lead to believe that it is ntfs format,  If so, you have 2 ready options:

[LIST]
[*]Change the partition file system to either ext4 or ext3 and do the install.
[*]Delete the partition and do the install.  Choose the "use unalloocated space" (or wording like that) during the installation.
[/LIST]

Hope this helps.

-IndyTim / DataMan

---

