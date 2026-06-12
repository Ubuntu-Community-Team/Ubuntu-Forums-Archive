---
title: "Another Backup Thread"
date: 2009-09-05
forum: General Help
---

### Post by theozzlives on 2009-09-05
I've modified the following to back up just my /home/ozzie:
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087"). I know I can exclude from the archive, but I want to include /var/www in my /home backup. I've been through the man pages (but may have missed something). How can I do this?

If someone has a better idea, I'm open. I just want to backup /home/ozzie and /var/www.

---

### Post by starcraft.man on 2009-09-05
Like Elzar says, [BAM]("https://help.ubuntu.com/community/BackupYourSystem/TAR")!

I happen to do an nice guide (or rather fix it up) on TAR. If you wanna keep it really simple, just back up those two folders in particular (i.e. see dissection of sample command, simply set the directory it starts backing up to other than root. Name em appropriately.

Otherwise, just exclude any folders in Var ya don't want, more of a hassle. That's why I'd just do the former.

---

