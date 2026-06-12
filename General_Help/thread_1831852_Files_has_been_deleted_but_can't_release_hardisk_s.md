---
title: "Files has been deleted but can't release hardisk size"
date: 2011-08-23
forum: General Help
---

### Post by thearetc on 2011-08-23
I really need your help,

I have a problem to gain my hardisk size after deleting a large amount of files. i have root partition size with 196 GB. actual used size in that partition is about 70GB, with command df -h, the used size 139GB. I have no idea to find out where is the hidden files. this happend after I delete the large amount of files because the hardisk almost full. the file i have deleted is almost 60 GB size.

Does anyone can help me please...

so much thank you...

---

### Post by Wim Sturkenboom on 2011-08-24
From the GUI, it ends in the trash; so clear the trash.

From command line, a program might still have the file in use; *_du_* will no longer see it but *_df_* will. Simplest in that case is to reboot your system. Slightly more difficult is to find the process that has the file in use and stop that process

---

### Post by lisati on 2011-08-24
*Thread moved to **General Help**.*

---

### Post by raja.genupula on 2011-08-24
all those deleted files will be stored in .Trash (A Hidden folder) in each and every folder . use ctrl+H to see that . what ever you deleted in a folder those will to send to that folder's .Trash folder . thats why even though you've deleted them ,  size will be not clear until you clear them from trash too .

---

