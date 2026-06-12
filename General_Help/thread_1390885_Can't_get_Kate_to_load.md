---
title: "Can't get Kate to load"
date: 2010-01-26
forum: General Help
---

### Post by grubby23 on 2010-01-26
Hi,

when trying to load Kate I get the following error message:

trying to create local folder /home/xxx/.kde/share: Permission denied
trying to create local folder /home/xxx/.kde/share: Permission denied
trying to create local folder /home/xxx/.kde/cache-desktop: Permission denied
...
kdeinit4: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/xxx/.kde/socket-desktop/kdeinit4__0'

Anyone an idea what is happening here and how I could resolve this issue.

Many thanks!

---

### Post by SuperSonic4 on 2010-01-26
It would appear that kate wants to write direct into the /home directory instead of into /home/user as it should. As root owns /home this makes sense.

No idea how to fix it though, perhaps deleting ~/.kde4/share/apps/kate would work?

---

### Post by ajgreeny on 2010-01-26
> trying to create local folder /home/xxx/.kde/share: Permission denied
trying to create local folder /home/xxx/.kde/share: Permission denied
trying to create local folder /home/xxx/.kde/cache-desktop: Permission denied
Assuming xxx is your username in the above quote, check the ownership and permissions of the folder /home/xxx/.kde to see if it belongs to you.  There does appear to be a problem with permissions for some reason, but more info is needed to suggest a solution.

---

### Post by rCXer on 2010-01-26
As others have suggested, this is a permissions problem.

Someone else reported [the same problem]("http://ubuntuforums.org/showthread.php?t=1387242") last week. Changing the permissions of the ~/.kde folder and _**all**_ its subfolders fixed this. (Look at the link for more details.)  Maybe we should file a bug report.

---

### Post by rCXer on 2010-01-26
After further research, I found these bug reports...
* [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/224859](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/224859)
* [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/289500](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/289500)
* [http://bugs.kde.org/show_bug.cgi?id=151219](http://bugs.kde.org/show_bug.cgi?id=151219)

Users in the first 2 reports say that running kate using sudo instead of gksudo/kdesudo breaks the permissions.

---

