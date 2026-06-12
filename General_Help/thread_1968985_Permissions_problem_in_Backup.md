---
title: "Permissions problem in Backup"
date: 2012-04-29
forum: General Help
---

### Post by arnstein99 on 2012-04-29
This is either a new problem in Ubuntu 12.04, or an improvement in error handling in U. 12.04.

I launch "Backup" from the Ubuntu "Settings" panel. I perform a backup to an external USB drive. The backup job is mostly successful, however a pop-up box appears at the end of the backup job. It informs me that several files were not backed up. These files are all in directory /boot, and they look important.

I examined these files, and they all have permission "-rw" for root, and "---" for all other users. This is almost certainly the problem.

I can think of two work-arounds:
1. Launch "Backup" with higher permissions.
2. Manually change the permissions of the problematic files in /boot.

I would prefer not to try work-around 2. The problematic files include files related to the latest version of Linux. I am inclined to believe that the Ubuntu installer "knew what it was doing" when it set the permissions on these files.

Any suggestions? Is this a bug that I should file against Ubuntu 12.04?

---

### Post by ppanish on 2012-06-14
I just upgraded from 11.10 and have experienced the same problem, however it applies to files distributed through the system, not just in /boot. Changing permissions on a per file basis is not an option.

Have you made any progress in resolving this issue?

---

### Post by arnstein99 on 2012-06-14
> **ppanish said:**
> Have you made any progress in resolving this issue? There is already an Ubuntu bug filed, and I added my comment to it: [https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/851771](https://bugs.launchpad.net/ubuntu/+source/deja-dup/+bug/851771) .  No action on that bug.

You can launch deja-dup yourself, with an sudo. That solves the immediate problem. However, I find that the deja-dup restore function has problems and this is bad. I filed this bug myself: [https://bugs.launchpad.net/deja-dup/+bug/994997](https://bugs.launchpad.net/deja-dup/+bug/994997) . No action on this bug either.  

If you are going to rely on deja-dup for backup, I suggest that you test its restore capabilities IMMEDIATELY. Me, I have given up on deja-dup.

---

### Post by fbicknel on 2012-06-14
I like to use duplicity for backup of /home and dump to back up / (root).  duplicity is the stuff under the hood of deja-dup.  or... deja-dup is a front end for duplicty.

I run both as root.

Wrote a little script to run them both at night from root's crontab.

I liked duplicity because I can compress and encrypt the /home backups.

I like dump because its verrrry simple but powerful, especially for backing up a filesystem like /.  If / blows up, you want something simple to get you up and running again.  Modern versions will automatically split files into handy chunk sizes (4.5GB fits on a dvd for storage offsite) and can do compression.

Bottom line: if you're backing up your stuff, you can run your backup as your user.  Backing up the system requires root access.

---

