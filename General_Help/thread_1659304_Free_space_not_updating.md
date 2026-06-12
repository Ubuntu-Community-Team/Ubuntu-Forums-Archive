---
title: "Free space not updating"
date: 2011-01-03
forum: General Help
---

### Post by andrecamp on 2011-01-03
Hi,

I have an external harddrive. When I delete files off of it, the free space doesn't get updated. Please help.I want to readd stuff to it, but it wont let me because it keeps saying the space is all used up when I know its not.

---

### Post by drs305 on 2011-01-03
The deleted files continue to take up space until the associated trash bin is emptied.

You can empty your trash by right clicking the Trash icon and "Empty Trash".

There is also trash in root's trash bin. The safest way to empty root's trash is to open a file browser as root and use SHIFT-DEL to remove the /root/.local/share/Trash folder. You can install an app called "nautilus-gksu" which will allow you to open a folder as the administrator by right clicking it in Nautilus.

Here's a bit I wrote about Trash a while ago:
[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by andrecamp on 2011-01-03
I try to delete that but no difference and look at this. The content and free space information dont equal the same.

---

### Post by drs305 on 2011-01-03
I see from the graphic it's labeled 'external'. It's possible the trash is stored in a folder called .Trash-1000 if it's a non-linux filesystem. That folder is a hidden file so make sure the file browser shows hidden files when looking for it.

If that doesn't help, it's time to work your way through another guide about disk space. ;-)

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Run through this to see if it's something other than trash that is taking up the space.

---

