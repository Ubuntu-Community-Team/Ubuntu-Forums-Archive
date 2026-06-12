---
title: "How to recover mysql data?"
date: 2009-10-15
forum: General Help
---

### Post by Guruprasad on 2009-10-15
My Ubuntu which had MYSQl-Server crashed due to EXT3 partition errors. I can access all the files from root partition using LIVE CD. I would like to copy the Mysql data using LIVE CD, then reinstall UBUNTU and then restore the MYSQL Data to the newly installed UBUNTU. Can anyone tell me how to do this?

---

### Post by yknivag on 2009-10-15
The data is (usually) at /var/lib/mysql/ if you can recover this then you should be able to copy it to a new location (so long as the two setups are the same).

However you may be able to fix the file system errors without re-installing by using fsck (but make sure you back up first).

---

