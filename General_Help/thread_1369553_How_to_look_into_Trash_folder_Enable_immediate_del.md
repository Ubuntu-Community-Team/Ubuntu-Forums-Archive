---
title: "How to look into Trash folder? Enable immediate deletion?"
date: 2010-01-01
forum: General Help
---

### Post by pstein on 2010-01-01
Where is the Trash folder where deleted files are moved?
I found no /dev/null
How can I tell Ubuntu: Wipe Trash folder on exit
How can I tell Ubuntu: Delete files immediately without 
moving them first to Trash folder?

---

### Post by scouser73 on 2010-01-01
Go into Nautilus and click **Edit** > **Preferences** > **Behaviour** & check the box **Include A Delete Command That Bypasses The Wastebasket**

That will delete files without having them in the Trash.

---

### Post by Leppie on 2010-01-01
holding the shift key while deleting bypasses the trash bin as well.

---

### Post by Portable_Jim on 2010-01-04
> **pstein said:**
> Where is the Trash folder where deleted files are moved?
**Short answer:** ~/.local/share/Trash
 **Long answer:** The Trash files are split up into the files (~/.local/share/Trash/files) and the metadata for the files (~/.local/share/Trash/info). Both the file and the meta-data need to be deleted in order to "empty the trash".

---

### Post by pstein on 2010-01-13
> **scouser73 said:**
> Go into Nautilus and click **Edit** > **Preferences** > **Behaviour** & check the box **Include A Delete Command That Bypasses The Wastebasket**
 That will delete files without having them in the Trash.
 
Ok, thank you. And what if I want deleted files first go to Trash BUT delete them all AUTOMATICALLY at shutdown time?
 
In other words how can I distinguish: 
- Delete files from Trash automatically at next shutdown
- Delete files from Trash never automatically - only manually by user
 
Peter

---

### Post by pstein on 2010-01-27
...no answer?

---

