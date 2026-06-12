---
title: "What does Cache subdirectory store in firefox?"
date: 2012-07-29
forum: General Help
---

### Post by arroy_0209 on 2012-07-29
Inside .mozilla directory there is a subdirectory named Cache. There are some empty subdirectories and some other files like "_CACHE_001_" which is DOS executable (device driver) Can anybody please tell if these are necessary or can I empty the Cache subdirectory? I use "click & clean " to erase my browsing data after each session of firefox. Still these are there in the Cache. is something wrong?

---

### Post by vasa1 on 2012-07-29
> **arroy_0209 said:**
> Inside .mozilla directory there is a subdirectory named Cache. There are some empty subdirectories and some other files like "_CACHE_001_" which is **DOS executable** (device driver) Can anybody please tell if these are necessary or can I empty the Cache subdirectory? I use "click & clean " to erase my browsing data after each session of firefox. Still these are there in the Cache. is something wrong?

Why don't you use Firefox itself to clear cache?

---

### Post by arroy_0209 on 2012-07-29
I have tried this: preference->privacy->clear all current history. The cache subdir still exists and its contents remain as usual. Is there any other option to clear cache?

---

### Post by vasa1 on 2012-07-29
> **arroy_0209 said:**
> I have tried this: preference->privacy->clear all current history. The cache subdir still exists and its contents remain as usual. Is there any other option to clear cache?
I suspect those files and folders don't contain user data and are technically required by Firefox.
You can delete the main Cache folder by hand from Nautilus and Firefox will just recreate it and the subdirectories when you next run Firefox.

---

### Post by Bobhuber on 2012-07-29
> **arroy_0209 said:**
> Inside .mozilla directory there is a subdirectory named Cache. There are some empty subdirectories and some other files like "_CACHE_001_" which is DOS executable (device driver) Can anybody please tell if these are necessary or can I empty the Cache subdirectory? I use "click & clean " to erase my browsing data after each session of firefox. Still these are there in the Cache. is something wrong?
No and there is no need to worry  about the entries that are left. The directory can be set up to run in memory if you have enough ram and will be deleted everytime you shut off the computer if you are concerned about it.

---

