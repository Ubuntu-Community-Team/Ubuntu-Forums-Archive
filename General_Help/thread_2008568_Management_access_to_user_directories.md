---
title: "Management access to user directories"
date: 2012-06-22
forum: General Help
---

### Post by cigtoxdoc on 2012-06-22
I own a small chemistry and toxicology consulting business.  I am moving to an all Ubuntu (12.04) environment, and the restrictions on root in a GUI environment are creating a problem.  I have set the following users: John (that's me), Suzi (secretary) and Jim (works half-day only).  I do most of my work after the paid staff leaves and often I need access to their documents.  I want to be able to move documents from my folder to/from Suzi's and Jim's folders with a GUI file manager.  In other words, I want read/write permission for my employees folders and subfolders.  In earlier versions of Ubuntu, I could log in as root and do the necessary trasks.

How do I set the file permissions?

John

---

### Post by HiImTye on 2012-06-23
here's two ways off the top of my head:

1. you could make them belong to one group and set *permissions* to *rwx* for *anyone in that group*. make yourself a member of that group
you will need to change the *group ownership *of those files to the new group

2. use *root* to transfer files. you will need to set *ownership* to the individual users afterwards

---

### Post by U202E on 2012-06-23
hmm..
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions?note=easy")
and give yourself the permission.

---

