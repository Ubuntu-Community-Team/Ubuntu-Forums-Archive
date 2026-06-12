---
title: "No permissions"
date: 2006-05-23
forum: General Help
---

### Post by rmco2003 on 2006-05-23
I've recently tried to delete files from windows, but it won't let me saying I don't have permission to delete them, then when I check the permissions it says there are none available. How can I delete these files? I can't even move them out of the wastebasket..

---

### Post by Phlosten on 2006-05-23
By default Linux looks at the files in the Windows Filesystem as needed root permissions to access. At least thats what I have always experienced. 

You either need to change permissions of files with the CHMOD command or you can do what you will with them by using 'sudo' at the command line.

---

### Post by unnes on 2006-05-23
I'm not sure if you mean that you're trying to delete files from a window (e.g. Nautilus) or from Windows.

If you're trying to delete from an NTFS (typical Windows XP) partition, you're out of luck. You'll have to do this from Windows. There are wrappers you can use to allow you to edit files on NTFS partitions in Linux, but they're a gamble at best.

---

