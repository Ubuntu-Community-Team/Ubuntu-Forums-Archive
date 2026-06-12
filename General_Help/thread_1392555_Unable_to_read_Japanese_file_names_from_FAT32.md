---
title: "Unable to read Japanese file names from FAT32"
date: 2010-01-28
forum: General Help
---

### Post by 2benglish on 2010-01-28
Ubuntu 9.10 is on ext4, XP is on NTFS and the data to be accessed by both OS is on FAT32.

Both systems have Japanese language support enabled, but I am unable to read the Japanese file names from the FAT32 partition when using Ubuntu.

Is there a fix for this?

Thanks.

---

### Post by Ugluk on 2010-01-28
Are you using 'utf8' option mounting that partition?

---

### Post by 2benglish on 2010-01-28
Thank you. 
I added that in pysdm and all appears to be fine now.

---

