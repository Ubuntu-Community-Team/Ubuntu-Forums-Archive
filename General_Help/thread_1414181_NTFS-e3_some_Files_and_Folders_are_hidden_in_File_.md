---
title: "NTFS-e3 some Files and Folders are hidden in File Browser"
date: 2010-02-23
forum: General Help
---

### Post by martensitephase on 2010-02-23
Dear Frnds

The NTFS-3g was working fine but suddenly I am not able to see some mounted windows files and folders through File browser. I can see those files and folders through command prompt but not through file browser.

Any suggestion?

my fstab file look likes

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=3f7e7501-5ca1-4bee-bbb4-6b9762d49a1a / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=b4b54663-ff09-4673-935d-3695be1fac40 none swap sw 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Crive ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Drive ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

