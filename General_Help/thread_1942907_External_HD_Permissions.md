---
title: "External HD Permissions"
date: 2012-03-18
forum: General Help
---

### Post by jim78 on 2012-03-18
Hi, I've just formatted my ext. hard drive with ext4 (and tried ext2), and now i cannot write to it. I've googled the problem and found one or two suggestions, but they didn't work. I've tried a few different chown/chmod commands and they don't seem to do anything. I don't know if it's important, but if i right click on the drive icon and go to the "permissions" page, it says "permissions of (drive name) could not be determined". 

Has anyone got any suggestions?

Thanks in advance.

---

### Post by jim78 on 2012-03-18
Solved.

cd /media, then sudo chmod -R 777 * seemed to work. But is that now going to apply to all drives that show up in the /media directory?

---

