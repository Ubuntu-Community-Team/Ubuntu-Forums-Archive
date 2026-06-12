---
title: "Cut and Paste to SMB share causes Desktop to vanish"
date: 2009-08-24
forum: General Help
---

### Post by MockY on 2009-08-24
Every time I cut and paste files to SMB shares, the Desktop goes blank and gets inactive (as in, I can't see any icons or mounts anymore). I can copy files just fine, but as soon as I move them, then I encounter this problem. This was the case with Intrepid as well. I have to restart Gnome in order for it to go back to normal. However, I can go to the Desktop folder via Nautilus in order to access the files located in that folder.
What is going on?

---

### Post by michy99 on 2009-08-24
It sounds like you are somehow switching to the root desktop, which is usually empty. Are you opening any graphical applications as root? If you do, you need to use gksudo instead of sudo.

---

### Post by MockY on 2009-08-24
No, I don't run any graphical applications as root. Even so, changing desktop just because I cut-and-paste a document to a SMB share sounds extremely odd and buggy. Also, I can't create or add anything on the Desktop once this happens. If it was a permission issue, I would probably be notified about it. Furthermore, the wallpaper stays the same. If it was changed to root, then it would use the default wallpaper and not the one I use.

---

### Post by MockY on 2009-09-03
I now found out that this is the case with regular SSH as well. I tested on different systems with different versions of Ubuntu...and it's all the same....so you guys simply must have that issue as well. One thing most of these "shares" have in common is that they are saved as a bookmark.

---

### Post by networkthinking on 2009-09-28
Hello,
I have the same problem.  Any fix?  How do you restart Gnome?

Wally

---

### Post by MockY on 2009-10-06
You can restart it by ctrl+alt+backspace (if you use any version prior to Jaunty) or simply log out and log in again.

And sadly, I have no fix for this. All I can hope for is that it is fixed in the next release. And considering that the next Gnome version mainly has bugfixes and not so many added features, I have high hopes that it will be fixed.

---

