---
title: "Tar problems"
date: 2012-08-09
forum: General Help
---

### Post by Azdour on 2012-08-09
Hi,

Ever since moving from Ubuntu 10.04 to Xubuntu 12.04 I've had problems with using tar for daily backups.

My first issue was tar v1.26 was falsely detecting files/directories had changed when I know they had not been changed: [http://ubuntuforums.org/showthread.php?t=2021364](http://ubuntuforums.org/showthread.php?t=2021364)

So I moved down to v1.22 and that seemed to work for a week but then it started to hang causing the processor to jump to 100% and each morning I would have to kill the process.

I've now moved to v1.23 but the problem I am now facing is that the log for the backup is reporting that verify finds contents differ for quite a few directories. Again I know these directories have not changed.

We never had any of these issues under Ubuntu 10.04. It is causing large logs to be created and our backup check script (that runs on the backup logs) is constantly reporting the warning to me. Of course I have to review this warning to check that it is not something else wrong with the backup.

I should note that to get tar v1.23 to run correctly I had to patch the source code and rebuild it: [http://lists.gnu.org/archive/html/bug-tar/2010-04/msg00023.html](http://lists.gnu.org/archive/html/bug-tar/2010-04/msg00023.html)

---

### Post by Azdour on 2012-08-28
Update: I have raised the bug with GNU Tar but I have nothing...

In the end I installed Ubuntu 10.04 on another machine and copied the tar (v1.22) from there to Xubuntu 12.04.

It looks like its working. So its definitely a problem with tar v1.26 that comes with 12.04...

---

