---
title: "restrict/allow user access to directories on ntfs mounted drive"
date: 2010-12-29
forum: General Help
---

### Post by thode on 2010-12-29
I want to add an extra user to my desktop. The user can mount ntfs drives but none of the directories/files are visible to that user unless I allowed them to be visible/accessible.

[SIZE="1"]In my situation, I want the user to be able to use my desktop and access audio/video/... on the ntfs drive but I prefer not to give access to personal folders.[/SIZE]

Thanks in advance.

---

### Post by Wtower on 2010-12-29
Hi,
Due to filesystem differences you can only change the permissions under with the ntfs driver is mounted. I believe you cannot change individual files or directories permissions.

---

### Post by WorMzy on 2010-12-29
You can't restrict access to specific folders on an NTFS partition, it's all or nothing.

You can use this tutorial to set up permissions.ownership on NTFS partitions:
[[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

