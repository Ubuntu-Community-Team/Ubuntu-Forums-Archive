---
title: "Unable to mount location; failed to retrieve share list from server"
date: 2010-10-18
forum: General Help
---

### Post by finsyourfriend on 2010-10-18
Greetings all.

THE HISTORY:

My network was running happily with no problems. After clicking "Places," then "Network," I double-clicked "Windows Network." My wife's laptop appeared merrily ready to be clicked. I browsed through and accessed the "Public" folder. Ubuntu auto-mounted the "Public" folder on the Windows Vista machine to the desktop. All was well.

THE REASON:

I wanted to change the icon to a disk so it would mimic a "mapped" drive like in Windows. I right-clicked the shared folder mounted on the desktop, clicked "Properties," and then clicked the picture of the folder. I then clicked through to "/usr/share/icons/Human/scalable/devices" and selected the "drive-harddisk.svg" icon. The icon changed and I could still browse. I unmounted and re-mounted the folder with no problems, then changed back the disk to the regular folder icon.

THE PROBLEM:

After restarting the computer, if I click "Places," then "Network," then double-click "Windows Network," I'm greeted with the following error message:

Unable to mount location. Failed to retrieve share list from server.

WORKAROUND:

Opening Firefox and typing smb://IP-of-wife's-laptop shows the share list. I can open and access the "Public" folder no problem.

Thoughts?

---

### Post by finsyourfriend on 2010-10-18
Sorry all. Please view this thread in the correct category 
under Networking & Wireless:
[URL="http://ubuntuforums.org/showthread.php?p=9993627#post9993627"]
http://ubuntuforums.org/showthread.php?p=9993627#post9993627[/URL]

---

